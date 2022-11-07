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

- **resources** - which resources should have their configuration monitored
- **rules** - which rules should be enabled to evaluate configuration
    - **conformance packs** - a set of rules and remediation actions
- **accounts** - which accounts should be monitored and how

#### Resources

For resources, we will configure AWS Config to monitor [all supported resource types](https://docs.aws.amazon.com/config/latest/developerguide/resource-config-reference.html).

#### Rules

To start, we will implement the 12 rules recommended by [this article](https://acloudguru.com/blog/engineering/12-aws-config-rules-that-every-account-should-have):

- **cloudformation-stack-drift-detection-check** - All stacks should have no drift
- **s3-bucket-level-public-acess-prohibited** - S3 buckets should not be public
- **ec2-instance-no-public-ip** - EC2 instances should not have public IPs
- **ebs-snapshot-public-restorable-check** - Your server snapshots should not be public
- **iam-root-access-key-check** - The root user should not have access keys
- **cloudtrail-enabled** - CloudTrail should always be enabled
- **ec2-ebs-encryption-by-default** - All EBS volumes should be encrypted by default
- **s3-bucket-server-side-encryption-enabled** - S3 should be encrypted by default
- **vpc-default-security-group-closed** - The default security group should not be in use
- **acm-certificate-expiration-check** - Ensure your certificates are not about to expire
- **access-keys-rotated** - Ensures IAM user access keys are rotated
- **iam-user-unused-credentials-check** - Find inactive accounts to disable

We will not use conformance packs because [they are not available in GovCloud](https://docs.aws.amazon.com/govcloud-us/latest/UserGuide/govcloud-config.html).