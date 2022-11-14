# AWS Security: Monitoring and Alerting

## Why

The cloud.gov platform is subject to periodic DDoS and probing attacks on our infrastructure. While the platform includes tooling at the VM-level like [AIDE](https://aide.github.io/) to detect intrusion and unexpected changes, currently we have limited tooling at the infrastructure provider-level (AWS) to monitor for malicious activity.

Thus, if a successful attack were able to "break out" from our VMs and start making changes to other AWS resources, we would currently have limited ability to recognize it and to respond.

In order to improve our security compliance and to mitigate our security risk, we would like to enable two AWS services:

- [AWS Config](https://aws.amazon.com/config/) - Monitors configuration for a broad range of AWS resources and reports compliance with configured rules. Can send alerts in response to configuration changes or changes in compliance status.
- [AWS GuardDuty](https://aws.amazon.com/guardduty/) - Continuously monitors AWS logs for malicious activity based on built-in threat intelligence. Creates Cloudwatch events for any findings.

## Implementation

### AWS Config

There are several things to consider when setting up AWS Config:

- **accounts** - which accounts should be monitored and how
- **resources** - which resources should be monitored
- **rules** - how should resource configuration be evaluated
- **notifications** - how to be notified about configuration changes or evaluation results

#### Accounts

We plan to enable AWS Config on all of our AWS accounts in both the commercial and the GovCloud partitions.

In both partitions, our AWS accounts are managed as part of [AWS organizations](https://aws.amazon.com/organizations/).

[AWS Config supports evaluating configuration rules and aggregating the results from multiple accounts, including all of the accounts in an AWS organization](https://docs.aws.amazon.com/config/latest/developerguide/aggregate-data.html). Before you can aggregate results from the member accounts into the aggregator account, you do have to **enable AWS Config in the member accounts**. And in GovCloud, [the feature to create rules for all accounts in an organization is disabled](https://docs.aws.amazon.com/govcloud-us/latest/UserGuide/govcloud-config.html#:~:text=AWS%20Config%20deployment%20of%20rules%20across%20an%20AWS%20Organization%20are%20not%20supported%20in%20AWS%20GovCloud%20(US).), so we have to create the rules we want aggregated separately in each member account (in reality this will be handled by Terraform and CI automation).

While you can use the management account of an AWS organization to aggregate Config results from the other accounts in the organization, this violates the security **principle of least privilege** which suggests that you should strictly limit permissions to only those necessary to do a job. Thus, aggregating Config results from the management account, which has broad-based permissions and access to other AWS accounts in the organization, would be too permissive.

Instead of using the management accounts, we will create new AWS accounts in both the commercial and GovCloud partitions solely for the purpose of managing security services that apply organization-wide. We will set up these new "security" AWS accounts as delegated administrators for AWS Config so that they can aggregate Config evaluations for all accounts in our AWS organizations. Here are some helpful AWS resources on setting up delegated administrators for AWS Config:

- <https://aws.amazon.com/blogs/mt/using-delegated-admin-for-aws-config-operations-and-aggregation/>
- <https://aws.amazon.com/blogs/mt/org-aggregator-delegated-admin/>

Currently, AWS Config is already enabled and configured in the commercial partition on the management account for the AWS organization (known as `com-root` in our account bookmarks and [`aws-admin` repo](https://github.com/cloud-gov/aws-admin)). **It is only configured to monitor resources in the management account and not as an aggregator for all the accounts in the AWS organization**.

The AWS organization for our commercial accounts is administered by TTS Tech Portfolio, not the cloud.gov team. Ultimately, we plan to set up our own AWS organization for our commercial accounts. The process of moving to an organization managed by the cloud.gov team could impact the aggregation for AWS Config. Furthermore, since almost all of our infrastructure lives in the GovCloud partition, not commercial, we are **not going to prioritize the work to set up AWS Config in the commercial partition**.

#### Resources

For resources, we will configure AWS Config to monitor [all supported resource types](https://docs.aws.amazon.com/config/latest/developerguide/resource-config-reference.html).

#### Rules

[AWS Config rules are specifications of the expected configuration for various AWS resources](https://docs.aws.amazon.com/config/latest/developerguide/evaluate-config.html).

To start, we will implement these AWS Config rules (inspired by [this article](https://acloudguru.com/blog/engineering/12-aws-config-rules-that-every-account-should-have)):

- **access-keys-rotated** - Ensures IAM user access keys are rotated
- **acm-certificate-expiration-check** - Ensure your certificates are not about to expire
- **cloudtrail-enabled** - CloudTrail should always be enabled
- **ebs-snapshot-public-restorable-check** - Your server snapshots should not be public
- **ec2-ebs-encryption-by-default** - All EBS volumes should be encrypted by default
- **ec2-instance-no-public-ip** - EC2 instances should not have public IPs
- **iam-no-inline-policy-check** - Checks that inline policy feature is not in use
- **iam-root-access-key-check** - The root user should not have access keys
- **iam-user-group-membership-check** - Checks whether IAM users are members of at least one IAM group.
- **iam-user-no-policies-check** - Checks that none of your IAM users have policies attached. IAM users must inherit permissions from IAM groups or roles.
- **iam-user-unused-credentials-check** - Find inactive accounts to disable
- **s3-bucket-public-read-prohibited** - S3 buckets should not be public
- **s3-bucket-server-side-encryption-enabled** - S3 should be encrypted by default
- **vpc-default-security-group-closed** - The default security group should not be in use

Unless otherwise noted, all rules that support evaluation on a periodic frequency will be set to evaluate every 24 hours.

#### Conformance packs

[Conformance packs are sets of rules and pre-defined remediation actions for resources that are not in compliance](https://docs.aws.amazon.com/config/latest/developerguide/conformance-packs.html).

**We will not use conformance packs because [they are not available in GovCloud](https://docs.aws.amazon.com/govcloud-us/latest/UserGuide/govcloud-config.html).**

#### Notifications

AWS Config can deliver notifications for a number of events: [changes in configuration on monitored resources, changes in compliance status on monitored resources, and more](https://docs.aws.amazon.com/config/latest/developerguide/notifications-for-AWS-Config.html).

Given the amount of deployed resources for cloud.gov and thus potential volume of notifications, to start with we will only enable notifications for resources that are not in compliance. [We will use EventBridge to filter for notifications about non-compliant resources and send them to a new SNS topic](https://aws.amazon.com/premiumsupport/knowledge-center/config-resource-non-compliant/).

To get the notifications from the SNS topic to our operations team, we will:

- Create a new Google group (`cloud-gov-security`) and suscribe the group email address to the topic

#### Responsibility

It is the responsibility of the platform engineer currently on the [maintenance rotation](https://cloud.gov/docs/ops/maintenance-list/) to assess incoming notifications and to address any issues that require immediate attention.

**Some notifications may not require immediate attention**, so they can wait until we have dedicated security engineers to address. It will always be possible to view which resources are out of compliance in our AWS Config dashboard.

If any notifications are assessed to constitute a security incident, then the maintenance engineer should initiate the [formal security incident process](https://cloud.gov/docs/ops/security-ir/).

## AWS GuardDuty

### Accounts

[As with AWS Config](#accounts), we will run AWS GuardDuty in a new "security" account in our AWS Organizations for both the commercial and GovCloud partitions. [This account will serve as a delegated administrator for managing AWS GuardDuty for all accounts within the organization](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_organizations.html).

[Once the GuardDuty administrator account is setup, we will link the other accounts in the AWS organization to it as member accounts](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_accounts.html#master_member_relationships).

As with AWS Config, we are only prioritizing the work to enable AWS GuardDuty for our GovCloud accounts.

### What to monitor

No specification of what to monitor is required for AWS GuardDuty. [Once GuardDuty is enabled, it automatically begins monitoring DNS logs, CloudTrail logs, and more](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_settingup.html#setup-before).

### Backing up findings

Findings are only backed in GuardDuty for a maximum of 90 days. [We could back up the findings to S3 for indefinite storage](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_settingup.html#setup-export).

### Notifications

[We will send GuardDuty notifications about findings to a new SNS topic](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_settingup.html#setup-sns). We will filter the events to only receive notifications about findings that are [moderate severity or greater](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings.html#guardduty_findings-severity), since low severity findings do not require remediation.

To deliver the notifications from SNS to our operations team, we will:

- Create a new Google Group (`cloud-gov-security`) and subscribe the group email address to the topic
- Send the notifications to the `#cg-aws-security` Slack channel

### Responsibility

Since we will configure GuardDuty to only send notifications for medium/high severity findings, any time we receive a notification about a finding, it should be taken very seriously.

The cloud.gov platform engineer currently on [the maintenance rotation](https://cloud.gov/docs/ops/maintenance-list/) will be the first person responsible to investigate any findings, but if they need assistance, they should pull in other team members for support as necessary. Addressing these findings should be treated as an "all hands on deck" event if necessary.

Engineers should use their discretion to assess whether it is appropriate to initiate the [formal security incident process](https://cloud.gov/docs/ops/security-ir/) as well.

## Implementation: Next steps

### Prerequisites

1. [Request a new `cloud-gov-security` Google Group](https://handbook.tts.gsa.gov/tools/google-groups/#create-a-google-group)
1. Request two new "security" AWS accounts from TTS Tech Portfolio, one each for the GovCloud and commercial partitions. These are the accounts that will be used as delegated administrators to manage AWS Config and AWS GuardDuty in the respective organizations within each partition.

### Config

1. Update the `cg-provision` repo to include Terraform code that is deployed in all of the GovCloud organization accounts
    - Reference for all accounts in the organization can be found here: <https://github.com/cloud-gov/aws-admin/blob/main/stacks/gov/sso/main.tf#L21>
1. Update the `cg-provision` code to create the following resources in all GovCloud accounts:
    - AWS Config settings: <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_configuration_recorder>
    - AWS Config delivery channel (should use an S3 bucket): <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_delivery_channel>
    - AWS Config rules: <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_config_rule>
1. Add code in `cg-provision` to create the AWS Config Aggregator in the GovCloud delegated administrator account
    - <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_configuration_aggregator>

### GuardDuty

1. Add code in `cg-provision` to enable AWS GuardDuty in the delegated administrator account
    - <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/guardduty_organization_admin_account>
    - <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/guardduty_organization_configuration>
1. Add code in `cg-provision` to link accounts as members of the GuardDuty
    - <https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/guardduty_member>