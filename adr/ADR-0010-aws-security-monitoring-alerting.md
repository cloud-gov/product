# AWS Security: Monitoring and Alerting

## Why

The cloud.gov platform is subject to periodic DDoS and probing attacks on our infrastructure. While the platform includes tooling at the VM-level like [AIDE](https://aide.github.io/) to detect intrusion and unexpected changes, currently we have limited tooling at the infrastructure provider-level (AWS) to monitor for malicious activity.

Thus, if a successful attack were able to "break out" from our VMs and start making changes to other AWS resources, we would currently have limited ability to recognize it and to respond.

In order to improve our security compliance and to mitigate our security risk, we would like to enable two AWS services:

- [AWS Config](https://aws.amazon.com/config/) - Monitors configuration for a broad range of AWS resources and reports compliance with configured rules. Can send alerts in response to configuration changes.
- [AWS GuardDuty](https://aws.amazon.com/guardduty/) - Continuously monitors AWS logs for malicious activity using machine learning. Creates Cloudwatch events for any findings.

## Implementation

### AWS Config

There are several things to consider when configuring AWS Config:

- **accounts** - which accounts should be monitored and how
- **resources** - which resources should be monitored
- **rules** - how should resource configuration be evaluated
- **notifications** - how to be notified about configuration changes or evaluation results

#### Accounts

We plan to enable AWS Config on all of our AWS accounts in both the commercial and the GovCloud partitions.

In both partitions, our AWS accounts are managed as part of [AWS organizations](https://aws.amazon.com/organizations/).

[AWS Config supports evaluating configuration rules and aggregating the results from multiple accounts, including all of the accounts in an AWS organization](https://docs.aws.amazon.com/config/latest/developerguide/aggregate-data.html).

While you can use the management account of an AWS organization to aggregate Config results from the other accounts in the organization, this violates the security **principle of least privilege** which suggests that you should strictly limit permissions to only those necessary to do a job. Thus, aggregating Config results from the management account, which has broad-based permissions and access to other AWS accounts in the organization, would be too permissive.

Instead of using the management accounts, we will create new AWS accounts in both the commercial and GovCloud partitions solely for the purpose of managing security services that apply organization-wide. We will set up these new "security" AWS accounts as [delegated administrators for AWS Config so that they can aggregate Config evaluations for all accounts in our AWS organizations](https://aws.amazon.com/blogs/mt/org-aggregator-delegated-admin/).

Currently, AWS Config is already enabled and configured in the commercial partition on the management account for the AWS organization (known as `com-root` in our account bookmarks and [`aws-admin` repo](https://github.com/cloud-gov/aws-admin)). **It is only configured to monitor resources in the management account and not as an aggregator for all the accounts in the AWS organization**.

The AWS organization for our commercial accounts is administered by TTS Tech Portfolio, not the cloud.gov team. Ultimately, we plan to set up our own AWS organization for our commercial accounts. The process of moving to an organization managed by the cloud.gov team could impact the aggregation for AWS Config. Furthermore, since almost all of our infrastructure lives in the GovCloud partition, not commercial, we are **not going to prioritize the work to set AWS Config in the commercial partition**.

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

We will not use conformance packs because [they are not available in GovCloud](https://docs.aws.amazon.com/govcloud-us/latest/UserGuide/govcloud-config.html).

#### Notifications

AWS Config can deliver notifications for a number of events: [changes in configuration on monitored resources, changes in compliance status on monitored resources, and more](https://docs.aws.amazon.com/config/latest/developerguide/notifications-for-AWS-Config.html).

Given the amount of deployed resources for cloud.gov and thus potential volume of notifications, to start with we will only enable notifications for resources that are not in compliance. [We will use EventBridge to filter the notifications and send them to a new SNS topic](https://aws.amazon.com/premiumsupport/knowledge-center/config-resource-non-compliant/). Using the SNS topic, we can create a subscription for a Google group email address  or we could send alerts to a dedicated Slack channel.

## AWS GuardDuty

