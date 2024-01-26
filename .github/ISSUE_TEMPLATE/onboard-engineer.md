---
name: Onboard New cloud.gov Engineer
title: Engineering Checklist for Onboarding (first name here)
about: Onboarding checklist for engineers. Pairs with a general onboarding checklist.
labels: ""
assignees: ""
---

# New Engineer Onboarding Checklist

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

## Google Groups and Spaces

- [ ] Business Unit Only - Add them to the [cloud.gov inquiries Google Group](https://groups.google.com/a/gsa.gov/forum/#!forum/cloud-gov-inquiries) so they can keep apprised of prospective new clients.

## Learn our policies and procedures

In addition to the topics in [the trainings section](#complete-cloudgov-trainings), review the following documents:

- [ ] Review the [cloud.gov open source policy guidance about protecting sensitive information](https://github.com/18F/open-source-policy/blob/master/practice.md#protecting-sensitive-information).
- [ ] Read the [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), particularly the [cloud.gov team responsibilities](https://cloud.gov/docs/ops/continuous-monitoring/#cloud-gov-team).
- [ ] Read the [Configuration Management Plan](https://cloud.gov/docs/ops/configuration-management/).
- [ ] Read the [cloud.gov Security Policies and Procedures](https://github.com/cloud-gov/cg-compliance-docs). These documents explain the high-level policies and procedures we must comply with while running cloud.gov, sorted into security control "families" They explain that we follow GSA IT security policy, and they provide a summary of the procedures in our System Security Plan.
- [ ] Review the System Security Plan (the latest version lives on [Google Drive](https://drive.google.com/drive/u/0/folders/0B6fPl5s12igNX3JwR2xFZVpmek0); look for "cloud.gov System Security Plan (SSP)" as a _.docx_ file). Of particular note for onboarding: Section 9 (System Description) and Section 10 (System Environment)
- [ ] Review the team's [Engineering Practices](https://github.com/cloud-gov/internal-docs/tree/main/docs/resources/Engineering-Practices). Some of these are mandatory because they fulfill FedRAMP requirements.

## Getting to know cloud.gov

Resources on cloud.gov:

- [ ] View the video: [A Technical Overview of cloud.gov](https://youtu.be/lwQCDeIm1Es)
- [ ] Read the [Delivery Process document](https://github.com/cloud-gov/product/blob/master/StoryLifecycle.md) to learn about how we work.
- [ ] Read our [service disruption guide](https://cloud.gov/docs/ops/service-disruption-guide/) to learn how we handle customer-facing service disruptions.

Resources on CloudFoundry/BOSH:

- [ ] Look at [Opensourced content for cloud foundry training classes: zero to hero (beginner), bosh/operator, and microservices](https://github.com/EngineerBetter/summit-training-classes)
- [ ] Here is some training materials: [GitHub - CloudCredo/training-operating-the-foundry: Training materials for Operating a Platform: BOSH and Everything Else](https://github.com/CloudCredo/training-operating-the-foundry)
- [ ] Very thorough documentation on BOSH: [Ultimate Guide to BOSH](https://ultimateguidetobosh.com/)
- [ ] [BOSH 101 presentation recording](https://drive.google.com/file/d/1CRYsgusiKnHm8p5wE8pi2ybcdsWKSqyA/view) and [slides](https://docs.google.com/presentation/d/1PN0MpcKGtwKlRZqh5Ol3kBYAi-LIYZY4MDFo61rZ97Y/edit?usp=drive_web&ouid=109379933856846715499)

Getting hands-on with cloud.gov:

- [ ] [Sign up for a cloud.gov sandbox](https://cloud.gov/sign-up/#get-trial-access-and-a-free-sandbox-space) using your GSA email address and start experimenting to get familiar with the basics of the PaaS from a user's perspective.
  - This is also required in order to make you a platform admin once you've completed the Cybersecurity and Privacy training.

## Engineering-specific items

### Machine admin rights

- [ ] In order to install development tools on your Mac, you will need to request local admin rights by [submitting a ServiceDesk ticket](https://docs.google.com/document/d/1xepZsh83lxPDykrb1NXoeHxj8m78qsdW-9KqzO_CHOQ/edit) using [this justification](https://docs.google.com/document/d/1YGid3pTji5W_M9RuF1GDf614BVkLIRDmSrt1tDbej-o/edit). If you're unable to create a ticket for yourself, your onboarding buddy can create one for you.

### Engineering account management

Before starting this section, you must complete:

1. GSA IT Security & Privacy Awareness Training
1. Role-based trainings listed under [Learn our policies and procedures](#learn-our-policies-and-procedures)

AWS user names should be identical across accounts so that permissions can be correctly managed by Terraform.

- [ ] Create [AWS Accounts](https://cloud.gov/docs/ops/aws-onboarding/) by following [these instructions](https://github.com/cloud-gov/aws-admin/blob/main/docs/user_mgmt.md). These accounts should be setup as read-only at the start, and once the 3 mandatory cloud.gov trainings are complete they will be switched to full admin accounts and added to the [audit input file](https://github.com/cloud-gov/cg-compliance/blob/master/audit/inputs.yml):
  - [ ] AWS Commercial accounts
  - [ ] AWS GovCloud accounts
  - [ ] Ensure new person has 60-day Google Calendar reminder to reset passwords
- [ ] Add them to Nessus Manager via the GUI
  - [ ] Add them to the ScanAdmins team in Settings > Groups

<details>
  <summary>
    Federal employees and staff contractors, expand this section:
  </summary>

You are a member of the Cloud Operations team, which means you have additional administrative permissions:

- [ ] [Make them an admin](https://cloud.gov/docs/ops/managing-users/#managing-admins) of the platform.
- [ ] Add them to the [`platform-ops`](https://github.com/orgs/cloud-gov/teams/platform-ops) team in GitHub.
- [ ] Add them as an admin on the cg-django-uaa [docs](https://readthedocs.org/projects/cg-django-uaa/)
- [ ] Add them to [our dockerhub org](https://hub.docker.com/orgs/cloudgov) and ensure we're not over our license count
- [ ] Add them as an `agent` to the cloud.gov support Zendesk (Ask a cloud.gov member with admin access to Zendesk to add them).
- [ ] Add them as Technical users to [Ubuntu Advantage](https://ubuntu.com/pro/users) (Admin users for leads and supervisors)

</details>

### Additional compliance setup/review

- [ ] Install `caulking` git leak prevention by following the [README](https://github.com/cloud-gov/caulking/blob/main/README.md)
- [ ] Verify `caulking` by running `make audit` and pasting a screenshot as a comment on this GitHub issue
- [ ] Set GPG signing set up for GitHub (instructions [here](https://docs.google.com/document/d/11UDxvfkhncyLEs-NUCniw2u54j4uQBqsR2SBiLYPUZc/edit)) and paste the output of `git config commit.gpgsign` as a comment on this GitHub issue

### Install a development environment for cloud.gov

> **Note:** Make sure you have followed the instructions in [Machine admin rights](#machine-admin-rights) at the top of this section to get local admin rights on your machine before moving forward

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

### Figure out your first tasks

Project contractors: Check in with your project lead about first tasks.

<details>
  <summary>
    Federal employees and staff contractors, expand this for instructions:
  </summary>

The engineering team currently contains the following squads, each with their own projects:

- Assurance, which focuses on security and compliance
- Platform, which maintains and improves cloud.gov, focusing on internals like our AWS architecture and Cloud Foundry
- Customer Success, which focuses on customer-facing features like service brokers and observability tools

If you are not already assigned to a particular squad, work with your onboarding buddy to join squad standups and learn what each squad is working on.

</details>

## Assurance-specific items

These items are only mandatory for someone stepping into an Assurance squad role, but you are welcome to subscribe even if you are on another squad:

- [ ] Subscribe to CISA alerts/updates: https://www.cisa.gov/about/contact-us/subscribe-updates-cisa
- [ ] Subscribe to FedRAMP mailing lists: https://public.govdelivery.com/accounts/USGSA/subscriber/topics?qsp=USGSA_2224
- [ ] Read Compliance Lead documents at root of the [Google Drive Security and Compliance](https://drive.google.com/drive/u/0/folders/1_vAXZsdVFYssR1DRCaavBCoDE_uxQCI5) folder
