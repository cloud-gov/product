# Architectural Decision Log

This log lists the architectural decisions for cloud.gov.

- [ADR-0001](https://github.com/cloud-gov/product/blob/master/adr/ADR-0001-egress-control.md) - Egress Control for tenants.
- [ADR-0002](https://github.com/cloud-gov/product/blob/master/adr/ADR-0002-container-to-container-encryption.md) - Container-to-Container encryption.
- [ADR-0003](https://github.com/cloud-gov/product/blob/master/adr/ADR-0003-static-ips.md) - Static IP for user apps.
- [ADR-0004](https://github.com/cloud-gov/product/blob/master/adr/ADR-0004-tcp-routes.md) - TCP Routing.
- [ADR-0005](#) - Idiomatic Bosh Building (in progress)
- [ADR-0006](https://github.com/cloud-gov/product/blob/master/adr/ADR-0006-commit-signing.md) - Git commit signing and validation
- [ADR-0007](https://github.com/cloud-gov/product/blob/master/adr/ADR-0007-container-scanning-and-validation.md) - Container Scanning & Validation.
- [ADR-0008](https://github.com/cloud-gov/product/blob/master/adr/ADR-0008-passive-dns.md) - Container Scanning & Validation.
- [ADR-0009](https://github.com/cloud-gov/product/blob/master/adr/ADR-0009-shield-advanced.md) - CloudFront and Shield Advanced.
- [ADR-0010](https://github.com/cloud-gov/product/blob/master/adr/ADR-0010-aws-security-monitoring-alerting.md) - AWS Security: Monitoring and Alerting

## Creating a new ADR

For new ADRs, please use [template.md](template.md).

## ADR review process

Since ADRs are meant to codify architectural decisions which will affect the entire platform and team, they should ideally be reviewed and approved by multiple team members. Since ADRs are often dense, they are usually better explained and understood in a group discussion than individual PR reviews. Furthemore, having multiple team members discuss an ADR increases the chances of identifying problems with the proposal.

Once a PR is created for an ADR, the ADR author should schedule a meeting, inviting cloud-gov@gsa.gov and cloud-gov-compliance@gsa.gov as optional attendees. In order for the meeting to proceed, a quorum of **3 team members is required**.

If 3 team members do not accept the invite, then try **re-scheduling the meeting one time**. If quorum cannot be met for the re-scheduled meeting, then the ADR review process can be handled by individual reviews on the PR.

## About ADRs

More information on MADR is available at <https://adr.github.io/madr/>.
General information about architectural decision records is available at <https://adr.github.io/>.
