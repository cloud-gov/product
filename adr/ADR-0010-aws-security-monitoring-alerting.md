# AWS Security: Monitoring and Alerting

## Why

The cloud.gov platform is subject to periodic DDoS and probing attacks on our infrastructure. While the platform includes tooling at the VM-level like [AIDE](https://aide.github.io/) to detect intrusion and unexpected changes, currently we have limited tooling at the infrastructure provider-level (AWS) to monitor for malicious activity.

Thus, if a successful attack were able to "break out" from our provisioned VMs and start making changes to other AWS resources, we would currently have limited ability to recognize it and to respond.

In order to improve our security compliance and to mitigate our security risk, we would like to enable two AWS services:

- [AWS Config](https://aws.amazon.com/config/) - Monitors configuration for a broad range of AWS resources and reports compliance with configured rules. Can send alerts in response to configuration changes.
- [AWS GuardDuty](https://aws.amazon.com/guardduty/) - Continuously monitors AWS logs for malicious activity using machine learning. Creates Cloudwatch events for any findings.

## Implementation

### AWS Config

