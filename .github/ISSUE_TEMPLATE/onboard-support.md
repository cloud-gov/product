---
name: Onboard New cloud.gov Support Team Member
title: Support Checklist for Onboarding (first name here)
about: This is the checklist and requirements for onboarding a new support team member to the cloud.gov team
labels: ""
assignees: ""
---

# New Support Team Member Onboarding Checklist

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

## Getting to know cloud.gov

These items will help you come up to speed on cloud.gov and what it is, how it works, why it exists, etc. While you
should take the time to go through them, please do not try and tackle it all in one shot! It can become overwhelming
very quickly, so your onboarding buddy will walk through this list with you at a high level with you to help manage the work.

- [ ] [Sign up for a cloud.gov sandbox](https://cloud.gov/sign-up/#get-trial-access-and-a-free-sandbox-space) using your GSA email address and start experimenting to get familiar with the basics of the PaaS from a user's perspective.
- [ ] Read our [service disruption guide](https://cloud.gov/docs/ops/service-disruption-guide/) to learn how we handle customer-facing service disruptions.

## Slack channels

Your onboarding buddy will add you to these Slack channels:

- [ ] `#cg-incidents` - private channel for incident response
- [ ] `#cg-ops-banter` - private channel for operations/engineering banter
- [ ] `#cg-priv-all` - private channel for in-team discussion

You will want to keep `#cg-support` unmuted so you are aware of requests from TTS-internal customers of cloud.gov.

## Support-specific items

- [ ] In order to install development tools on your Mac, you will need to request local admin rights by [submitting a ServiceDesk ticket](https://docs.google.com/document/d/1xepZsh83lxPDykrb1NXoeHxj8m78qsdW-9KqzO_CHOQ/edit) using [this justification](https://docs.google.com/document/d/1YGid3pTji5W_M9RuF1GDf614BVkLIRDmSrt1tDbej-o/edit). If you're unable to create a ticket for yourself, your onboarding buddy can create one for you.

### Additional compliance setup/review

- [ ] Install `caulking` git leak prevention by following the [README](https://github.com/cloud-gov/caulking/blob/master/README.md)
- [ ] Verify `caulking` by running `make audit` and pasting a screenshot as a comment on this GitHub issue
- [ ] Set GPG signing set up for GitHub (instructions [here](https://docs.google.com/document/d/11UDxvfkhncyLEs-NUCniw2u54j4uQBqsR2SBiLYPUZc/edit))

### Install a development environment for cloud.gov

- [ ] Install [Homebrew (`brew`)](https://brew.sh/)
- [ ] Install [CloudFoundry for mac per their docs](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html#pkg-mac):
  - `brew tap cloudfoundry/tap`
  - `brew install cf-cli@8`
  - `brew install openssl`
- [ ] Verify CloudFoundry Installation via the CLI (once an existing cloud.gov teammate has [made your cloud.gov admin account](https://cloud.gov/docs/ops/managing-users/#creating-admins))
  - `cf login -a api.fr.cloud.gov --sso`
  - `cf orgs`
    - As a cloud.gov support team member, you should have access to your sandbox; if you don't, please reach out to your onboarding buddy
