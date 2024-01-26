---
name: Onboard New cloud.gov Compliance Team Member
title: Compliance Checklist for Onboarding (first name here)
about: This is the checklist and requirements for onboarding a new compliance team member to the cloud.gov team
labels: ""
assignees: ""
---

# New Compliance Team Member Onboarding Checklist

## Special Notes

- [ ] Paste a link to the general onboarding ticket, which includes the onboarding authorization, here:

---

## Complete additional cloud.gov trainings

<details>
  <summary>
    Federal employees and staff contractors, expand this section. Not applicable to project contractors.
  </summary>

Engineers who are federal employees or staff contractors have a Contingency Plan role and may participate in Incident Response, so they must complete the CP and IR trainings. Project contractors do not need to complete these trainings. Check one of the following:

- [ ] Coordinate with your onboarding buddy to schedule Contingency Planning training within 60 days. (and annually after that). This will cover the following document, which you should also review before or after training:
  - [ ] Read the [Contingency Plan](https://docs.cloud.gov/ops/contingency-plan/).
- [ ] Coordinate with your onboarding buddy to schedule [Incident Response Training](https://docs.google.com/presentation/d/1AZjQE8zBzMRWZIFUuJPkJLted1ykGtALrLPoPRx5Vls/edit#slide=id.p) within 60 days of joining the team (and annually after that). This will cover the following document, which you should also review before or after training:
  - [ ] Read the [Incident Response Guide](https://cloud.gov/docs/ops/security-ir/).

</details>

## Learn our policies and procedures

- [ ] Review the [cloud.gov open source policy guidance about protecting sensitive information](https://github.com/18F/open-source-policy/blob/master/practice.md#protecting-sensitive-information).
- [ ] Read the [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), particularly the [cloud.gov team responsibilities](https://cloud.gov/docs/ops/continuous-monitoring/#cloud-gov-team).
- [ ] Read the [Configuration Management Plan](https://cloud.gov/docs/ops/configuration-management/).
- [ ] Read the [cloud.gov Security Policies and Procedures](https://github.com/cloud-gov/cg-compliance-docs). These documents explain the high-level policies and procedures we must comply with while running cloud.gov, sorted into security control "families" They explain that we follow GSA IT security policy, and they provide a summary of the procedures in our System Security Plan.
- [ ] Review the System Security Plan (the latest version lives on [Google Drive](https://drive.google.com/drive/u/0/folders/0B6fPl5s12igNX3JwR2xFZVpmek0); look for "cloud.gov System Security Plan (SSP)" as a _.docx_ file). Of particular note for onboarding: Section 9 (System Description) and Section 10 (System Environment)

## Slack channels

Project contractors: Your buddy will add you to the private channel for your project.

<details>
  <summary>
    Federal employees and staff contractors, expand this section:
  </summary>

Your onboarding buddy will add you to these Slack channels:

- [ ] `#cg-aws-security` - private channel where bots post security notices
- [ ] `#cg-billing` - private business development channel (if applicable)
- [ ] `#cg-incidents` - private channel for incident response
- [ ] `#cg-ops-banter` - private channel for operations/engineering banter
- [ ] `#cg-priv-all` - private channel for in-team discussion
- [ ] `#cg-priv-compliance` - private channel for security and compliance discussions

</details>

You might also be interested in these channels:

- [ ] `#g-security-compliance` - Channel for the Security & Compliance guild
- [ ] `#dev` - general chat for all TTS engineers

## Google Groups

- [ ] [cloud.gov Compliance](https://groups.google.com/a/gsa.gov/g/cloud-gov-compliance/members) (external-facing email address for communications with FedRAMP and others)

## Getting to know cloud.gov

These items will help you come up to speed on cloud.gov and what it is, how it works, why it exists, etc. While you
should take the time to go through them, please do not try and tackle it all in one shot! It can become overwhelming
very quickly, so your onboarding buddy will walk through this list with you at a high level with you to help manage the work.

- [ ] Read [the team onboarding document](https://github.com/cloud-gov/product/blob/main/Onboarding.md) for more context about cloud.gov.
- [ ] Bookmark the [pertinent links listed here](https://github.com/cloud-gov/product/blob/main/PertinentLinks.md).
- [ ] Read through [the Overview section of our site](https://cloud.gov/docs/overview/what-is-cloudgov/) for a broader understanding of cloud.gov, especially how we present it to potential customers and users.
- [ ] [Sign up for a cloud.gov sandbox](https://cloud.gov/sign-up/#get-trial-access-and-a-free-sandbox-space) using your GSA email address and start experimenting to get familiar with the basics of the PaaS from a user's perspective.
  - This is also required in order to make you a platform admin once you've completed the Cybersecurity and Privacy training.
- [ ] Read the [Delivery Process document](https://github.com/cloud-gov/product/blob/main/StoryLifecycle.md) to learn about how we work.
- [ ] Read our [service disruption guide](https://cloud.gov/docs/ops/service-disruption-guide/) to learn how we handle customer-facing service disruptions.

## Compliance-role specific items

### Machine admin rights

- [ ] In order to install development tools on your Mac, you will need to request local admin rights by [submitting a ServiceDesk ticket](https://docs.google.com/document/d/1xepZsh83lxPDykrb1NXoeHxj8m78qsdW-9KqzO_CHOQ/edit) using [this justification](https://docs.google.com/document/d/1YGid3pTji5W_M9RuF1GDf614BVkLIRDmSrt1tDbej-o/edit). If you're unable to create a ticket for yourself, your onboarding buddy can create one for you.

### Other tooling and access for compliance

- [ ] New person: Request Microsoft Office, per [TTS handbook instructions](https://handbook.tts.gsa.gov/tools/office/)
- [ ] **Compliance lead only**: Request access to cloud.gov's FedRAMP repository in max.gov by email to <info@fedramp.gov>.

### Cloud Operations account management

Before starting this section, you must complete:

1. GSA IT Security & Privacy Awareness Training
1. Role-based trainings listed under [Learn our policies and procedures](#learn-our-policies-and-procedures)

AWS user names should be identical across accounts so that permissions can be correctly managed by Terraform.

- [ ] Create [AWS Accounts](https://cloud.gov/docs/ops/aws-onboarding/) via the AWS web console (not Terraform) and provide one-time credentials - these will be setup with read-only/auditor permissions, and once the 3 mandatory cloud.gov trainings are complete they will be added to the [audit input file](https://github.com/cloud-gov/cg-compliance/blob/master/audit/inputs.yml):
  - [ ] AWS Commercial accounts
  - [ ] AWS GovCloud accounts
- [ ] Add them to Nessus Manager via the GUI
  - [ ] Add them to the ScanAdmins team in Settings > Groups
- [ ] [Make them an admin](https://cloud.gov/docs/ops/managing-users/#managing-admins) of the platform.
- [ ] Add them to the [`platform-ops`](https://github.com/orgs/cloud-gov/teams/platform-ops) team in GitHub.
- [ ] Add them to [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov) so they can participate in team-wide internal communication.
- [ ] Add them to the `cloud-gov-assurance-team` Google Group for meeting invites and communications
- [ ] Add them to [our dockerhub org](https://hub.docker.com/orgs/cloudgov) and ensure we're not over our license count

Your onboarding buddy will create a separate ticket tied to this one to track the AWS accounts being granted full admin access.

### Additional compliance setup/review

- [ ] Install `caulking` git leak prevention by following the [README](https://github.com/cloud-gov/caulking/blob/main/README.md)
- [ ] Verify `caulking` by running `make audit` and pasting a screenshot as a comment on this GitHub issue
- [ ] Set GPG signing set up for GitHub (instructions [here](https://docs.google.com/document/d/11UDxvfkhncyLEs-NUCniw2u54j4uQBqsR2SBiLYPUZc/edit))

### Install a development environment for cloud.gov

- [ ] Install [Homebrew (`brew`)](https://brew.sh/)
- [ ] Clone [the product repo](https://github.com/cloud-gov/product), `cd` into it, and run `brew bundle install` to install everything in `Brewfile`.
- [ ] Verify CloudFoundry installation via the CLI (once an existing cloud.gov teammate has [made your cloud.gov admin account](https://cloud.gov/docs/ops/managing-users/#creating-admins))
  - `cf login -a api.fr.cloud.gov --sso`
  - `cf orgs`
    - As a cloud.gov team member, you should have a long list of organizations
    - If you have none or one (e.g. sandbox) org, please reach out to your onboarding buddy
- [ ] Configure `aws-vault` by [following our directions](https://cloud.gov/docs/ops/secrets/#aws-credentials)
- [ ] Fix `fly`, the Concourse CLI, by running `xattr -d com.apple.quarantine /opt/homebrew/bin/fly`. Concourse does not sign `fly` with an Apple Developer account, so you must use `xattr` to manually remove the binary from quarantine. Verify by running `fly -h` in your command line.
- [ ] Install cloud.gov dev tools by cloning the [`cg-scripts` repo](https://github.com/cloud-gov/cg-scripts/): run `git clone https://github.com/cloud-gov/cg-scripts.git` in your command line

## Security and Compliance News

- [ ] Subscribe to CISA alerts/updates: <https://www.cisa.gov/about/contact-us/subscribe-updates-cisa>
- [ ] Subscribe to FedRAMP mailing lists: <https://public.govdelivery.com/accounts/USGSA/subscriber/topics?qsp=USGSA_2224>
- [ ] **Compliance Lead only**: Read Compliance Lead documents at root of the [Google Drive Security and Compliance](https://drive.google.com/drive/u/0/folders/1_vAXZsdVFYssR1DRCaavBCoDE_uxQCI5) folder
