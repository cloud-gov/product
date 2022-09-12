---
name: Onboard New cloud.gov Platform Operations Team Member
title: Checklist for Onboarding a New Platform Operator
about: This is the checklist and requirements for onboarding a new platform operator to the cloud.gov team
labels: ''
assignees: ''

---

# New Platform Operator Onboarding Checklist

## Special Notes

- **Do not create this issue until the System Owner has formally authorized and requested it.**
- **Please only use first names.**

---

In order to get `New Person` productively contributing to the cloud.gov team, `Buddy` should help `New Person` complete a prescribed set of tasks that will bring them up to speed and get them setup with cloud.gov.

## Instructions

1. Try to go through the checklists in order.
2. If `Buddy` can’t complete any of the items on their checklist personally, _they are responsible for ensuring that someone with the correct access completes that item_.

## Onboarding Checklist

### Required items for all team members

These items help us fulfill security and compliance requirements (including for FedRAMP). If you get stuck, or if these requirements are confusing, ask for help from your buddy or in a cloud.gov channel.

- [ ] Take judicious notes on what about this onboarding process or cloud.gov is confusing or frustrating. If you notice a problem (especially with things like documentation), you are more than welcome to fix it! At the very least, please share this information with your onboarding buddy (or someone) at some point so we can make the team/platform better. (You can also file issues and pull requests on [the template Onboarding checklist](https://github.com/cloud-gov/product/blob/master/.github/ISSUE_TEMPLATE/platform-ops-member-onboarding.md).
- [ ] Be sure to introduce yourself and follow up with your onboarding buddy (they should have reached out to you at this point; if they haven't, please let the team know) and make sure this issue is assigned to them in our [Github Project Planning Board](https://github.com/orgs/cloud-gov/projects/27/views/1). We use this board to organize, prioritize, and track our work.

#### Pre-requisites

- [ ] Complete [GSA OLU](https://gsaolu.gsa.gov/) GSA Mandatory Cyber Security and Privacy Training, including accepting the GSA IT Rules of Behavior, which is required before we can give you access to any cloud.gov systems. If you joined GSA more than two months ago, you've already completed this task and can just check the box.

#### Fulfill security and compliance requirements (including for FedRAMP) - Completed by onboarding buddy

- [ ] Make sure they're in [the list of people working on the project](https://docs.google.com/spreadsheets/d/187663k5MYJBNlKExLu_nhuovcZQfIbqYCu2n4noNY1o/edit#gid=0).
- [ ] Add their name, whether they're Cloud Ops (Platform), and the date they joined the team to the [training tracker](https://docs.google.com/spreadsheets/d/1hqU6cNeEB293OT0j3OvbdAFRkrf2zDOrPVxGfnr4sSw/edit#gid=0). Copy the formulas for the due dates from an existing row (grab the "corner" of the cells and pull down).
- [ ] As they complete training, fill out their completion dates in the [training tracker](https://docs.google.com/spreadsheets/d/1hqU6cNeEB293OT0j3OvbdAFRkrf2zDOrPVxGfnr4sSw/edit#gid=0).
- [ ] Add them to the @cloud-gov-team [in Slack’s Team Directory](https://get.slack.help/hc/en-us/articles/212906697-User-Groups#edit-a-user-group).
- [ ] Review the recurring cloud.gov meetings that are relevant for them in [the team calendar](https://calendar.google.com/calendar/embed?src=gsa.gov_0samf7guodi7o2jhdp0ec99aks@group.calendar.google.com&amp;ctz=America/Los_Angeles) (they will get access to this when added to the cloud.gov Team Google Group).
- [ ] Add them to the [`cloud-gov`](https://github.com/orgs/cloud-gov/people) organization in GitHub, and the [`cloud-gov-team`](https://github.com/orgs/cloud-gov/teams/cloud-gov-team) team.

#### Learn our policies and procedures

For the three trainings list at the top, your onboarding buddy will create a separate ticket to track the trainings once scheduling has been finished.  This will help consolidate trainings for multiple new members to the team and prevent them from blocking progress on this onboarding ticket.  Once the trainings are scheduled, they can be marked as complete here.

- [ ] Coordinate with your onboarding buddy to go through Contingency Planning training within 60 days (and annually after that). This will cover the following document, which you should also review before or after training:
  - [ ] Read the [Contingency Plan](https://docs.cloud.gov/ops/contingency-plan/).
- [ ] Coordinate with your onboarding buddy to go through [Incident Response Training](https://docs.google.com/presentation/d/1AZjQE8zBzMRWZIFUuJPkJLted1ykGtALrLPoPRx5Vls/edit#slide=id.p) within 60 days of joining the team (and annually after that). This will cover the following document, which you should also review before or after training:
  - [ ] Read the [Incident Response Guide](https://cloud.gov/docs/ops/security-ir/).
- [ ] Coordinate with your onboarding buddy to go through [nonpublic information training](https://docs.google.com/presentation/d/1uB4MlGCu8ZYUxjKVZKwicQ95MvLxaT4Mh93y6w79GPw/edit#slide=id.p) within 60 days of joining the team (and annually after that). This will cover the following documents, which you should also review before or after training:
  - [ ] Review the [cloud.gov open source policy guidance about protecting sensitive information](https://github.com/18F/open-source-policy/blob/master/practice.md#protecting-sensitive-information).
  - [ ] Read our [sharing secret keys](https://cloud.gov/docs/ops/secrets/#sharing-secret-keys) policy.
  - [ ] Review the [TTS requirements for password management](https://handbook.tts.gsa.gov/general-information-and-resources/tech-policies/password-requirements/).
- [ ] Read the [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), particularly the [cloud.gov team responsibilities](https://cloud.gov/docs/ops/continuous-monitoring/#cloud-gov-team).
- [ ] Read the [Configuration Management Plan](https://cloud.gov/docs/ops/configuration-management/).
- [ ] Read the [cloud.gov Security Policies and Procedures](https://github.com/cloud-gov/cg-compliance-docs). These documents explain the high-level policies and procedures we must comply with while running cloud.gov, sorted into security control "families" They explain that we follow GSA IT security policy, and they provide a summary of the procedures in our System Security Plan.
- [ ] Review the System Security Plan (the latest version lives on [Google Drive](https://drive.google.com/drive/u/0/folders/0B6fPl5s12igNX3JwR2xFZVpmek0); look for "cloud.gov System Security Plan (SSP)" as a _.docx_ file). Of particular note for onboarding: Section 9 (System Description) and Section 10 (System Environment)

### Getting to know cloud.gov

These items will help you come up to speed on cloud.gov and what it is, how it works, why it exists, etc.  While you
should take the time to go through them, please do not try and tackle it all in one shot!  It can become overwhelming
very quickly, so your onboarding buddy will walk through this list with you at a high level with you to help manage the work.

- [ ] View the video: [A Technical Overview of cloud.gov](https://youtu.be/lwQCDeIm1Es)
- [ ] Look at [Opensourced content for cloud foundry training classes: zero to hero (beginner), bosh/operator, and microservices](https://github.com/EngineerBetter/summit-training-classes)
- [ ] Here is some training materials: [GitHub - CloudCredo/training-operating-the-foundry: Training materials for Operating a Platform: BOSH and Everything Else](https://github.com/CloudCredo/training-operating-the-foundry)
- [ ] This gives a good overview of Bosh [Welcome - Ultimate Guide to BOSH](https://ultimateguidetobosh.com/)
- [ ] Read [the team onboarding document](https://github.com/cloud-gov/product/blob/master/Onboarding.md) for more context about cloud.gov.
- [ ] Bookmark the [pertinent links listed here](https://github.com/cloud-gov/product/blob/master/PertinentLinks.md).
- [ ] Read through [the Overview section of our site](https://cloud.gov/docs/overview/what-is-cloudgov/) for a broader understanding of cloud.gov, especially how we present it to potential customers and users.
- [ ] [Sign up for a cloud.gov sandbox](https://cloud.gov/sign-up/#get-trial-access-and-a-free-sandbox-space) using your GSA email address and start experimenting to get familiar with the basics of the PaaS from a user's perspective.
  - This is also required in order to make you a platform admin once you've completed the Cybersecurity and Privacy training.
- [ ] Read the [Delivery Process document](https://github.com/cloud-gov/product/blob/master/StoryLifecycle.md) to learn about how we work.
- [ ] Read our [service disruption guide](https://cloud.gov/docs/ops/service-disruption-guide/) to learn how we handle customer-facing service disruptions.
- [ ] Add the [cloud.gov Google Drive folder](https://drive.google.com/drive/folders/0Bx6EvBXVDWwheUtVckVnOE1pRzA) to your Google Drive -- that's where we put cloud.gov docs. If you create or move a doc there, it'll get the right access permissions for team members to be able to view and edit it.
- [ ] Subscribe to [the cloud.gov team calendar](https://calendar.google.com/calendar/embed?src=gsa.gov_0samf7guodi7o2jhdp0ec99aks@group.calendar.google.com&amp;ctz=America/Los_Angeles) (click the + in the bottom right) so you know when assorted team meetings are happening in the various squads. Tip: When you plan Out of Office time, make a calendar event for that on the cloud.gov calendar so that your teammates know you'll be away

### Slack channels

Your onboarding buddy will add you to these Slack channels:

- [ ] `#cloud-gov` - bots post announcements here
- [ ] `#cg-billing` - private business development channel (if applicable)
- [ ] `#cg-business` - business development (if applicable)
- [ ] `#cg-compliance` - compliance-related information and discussion
- [ ] `#cg-offtopic` - off-topic team sharing
- [ ] `#cg-platform` - platform operations
- [ ] `#cg-platform-news` - bots post platform alerts
- [ ] `#cg-general` - program-level information and discusion
- [ ] `#cg-support` - support requests and assistance within TTS
- [ ] `#cg-incidents` - private channel for incident response
- [ ] `#cg-priv-all` - private channel for in-team discussion
- [ ] `#cg-priv-gov` (Federal employees only) - may contain discussion of contracting-related or other private, federal-employee-only comms

Once you're added to these channels, you probably want to mute these channels until you're on support rotation:

- [ ] `#cg-support` - support requests and assistance within TTS
- [ ] `#cg-platform-news` - platform alerts

## Platform-Ops-specific items

You should already have admin rights on your machine as a part of its original setup.  If for whatever reason you don't,
Please let your onboarding buddy know and they will help you request [local admin rights](https://docs.google.com/document/d/1xepZsh83lxPDykrb1NXoeHxj8m78qsdW-9KqzO_CHOQ/edit) on your GFE Mac using [this justification](https://docs.google.com/document/d/1YGid3pTji5W_M9RuF1GDf614BVkLIRDmSrt1tDbej-o/edit).

### Cloud Operations account management

_Note: These are all contingent on completing the GSA Mandatory Cyber Security and Privacy Training first. AWS user names should be identical across accounts so that permissions can be correctly managed by Terraform._

- [ ] Create [AWS Accounts](https://cloud.gov/docs/ops/aws-onboarding/) by following [these instructions](https://github.com/cloud-gov/aws-admin/blob/main/docs/user_mgmt.md). These will be setup as read-only at the start, and once the 3 mandatory cloud.gov trainings are complete they will be switched to full admin accounts and added to the [audit input file](https://github.com/cloud-gov/cg-compliance/blob/master/audit/inputs.yml):
  - [ ] AWS Commercial accounts
  - [ ] AWS GovCloud accounts
- [ ] Add them to Nessus Manager via the GUI
- [ ] [Make them an admin](https://cloud.gov/docs/ops/managing-users/#managing-admins) of the platform.
- [ ] Add them to the [`platform-ops`](https://github.com/orgs/cloud-gov/teams/platform-ops) team in GitHub.
- [ ] Add them as an admin on the cg-django-uaa [docs](https://readthedocs.org/projects/cg-django-uaa/)
- [ ] Add them to [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov) so they can participate in team-wide internal communication.
- [ ] Add them to [our dockerhub org](https://hub.docker.com/orgs/cloudgov) and ensure we're not over our license count
- [ ] Add them as an `agent` to the cloud.gov support Zendesk (Ask a cloud.gov member with admin access to Zendesk to add them).
- [ ] Business Unit Only - Add them to the [cloud.gov inquiries Google Group](https://groups.google.com/a/gsa.gov/forum/#!forum/cloud-gov-inquiries) so they can keep apprised of prospective new clients.

Your onboarding buddy will create a separate ticket tied to this one to track the AWS accounts being granted full admin access.

### Additional compliance setup/review

- [ ] Install `caulking` git leak prevention by following the [README](https://github.com/cloud-gov/caulking/blob/master/README.md)
- [ ] Verify `caulking` by running `make audit` and pasting a screenshot as a comment on this GitHub issue
- [ ] Set GPG signing set up for GitHub (instructions [here](https://docs.google.com/document/d/11UDxvfkhncyLEs-NUCniw2u54j4uQBqsR2SBiLYPUZc/edit)) and paste the output of `git config commit.gpgsign` as a comment on this GitHub issue
- [ ] Run [this script](https://github.com/cloud-gov/cg-scripts/blob/master/write-pgp-pub-key-s3.sh)
to upload your GPG key to an S3 bucket containing the trusted keys for our team

### Install a development environment for cloud.gov

- [ ] Install [Homebrew (`brew`)](https://brew.sh/)
- [ ] Install [CloudFoundry for mac per their docs](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html#pkg-mac):
  - `brew tap cloudfoundry/tap`
  - `brew install cf-cli@7`
  - `brew install openssl`
- [ ] Verify CloudFoundry Installation via the CLI (once an existing cloud.gov teammate has [made your cloud.gov admin account](https://cloud.gov/docs/ops/managing-users/#creating-admins))
  - `cf login -a api.fr.cloud.gov --sso`
  - `cf orgs`
    - As a cloud.gov team member, you should have a very giant list of organizations
    - If you have none or one (e.g. sandbox) org, please reach out to your onboarding buddy
- [ ] Install the [Bosh CLI using their instructions for MacOS](https://bosh.io/docs/cli-v2-install/#using-homebrew-on-macos)
  - `brew install cloudfoundry/tap/bosh-cli`
  - [ ] Verify the installation by running `bosh -v` in the command line
- [ ] Install Terraform and other tools per [cg-provision](https://github.com/cloud-gov/cg-provision)
  - `brew install terraform`
  - `brew install awscli`
  - `brew install jq`
  - [ ] Verify Terraform installed and is in your path: run `terraform` and helper text should display
  - [ ] Verify AWS CLI installed and is in your path: run `aws` and helper text should display
- [ ] Install and configure `aws-vault` by [following our directions](https://cloud.gov/docs/ops/secrets/#install-aws-vault-for-aws-credentials-and-create-a-profile)
- [ ] Install the Concourse `fly` CLI
  - `brew install fly`
  - [ ] Verify by running `fly -h` in your command line
    - This may fail due to app security policy on your mac rejecting apps from unidentified developers. To fix it (replace `<VERSION>` with your installed version of `fly`):

      `xattr -d com.apple.quarantine /usr/local/Caskroom/fly/<VERSION>/fly`
- [ ] Install cloud.gov dev tools by cloning the [`cg-scripts` repo](https://github.com/cloud-gov/cg-scripts/): run `git clone https://github.com/cloud-gov/cg-scripts.git` in your command line

### Figure out your first tasks

Please work with your onboarding buddy to determine a platform component to work on first.
Once you've identified the component you're going to focus on, your onboarding buddy will introduce
you to someone who can onboard you to that project in specific. For the next few sprints, work on features,
bugs, and improvements on this component. Reach out to your onboarding buddy or anyone else on the team
if you need any help. Here are some easily-separated pieces to consider:

- S3 broker (Golang, Open Service Broker API)
- Aws broker (Golang, Open Service Broker API)
- Domain brokers and friends (New stuff is all python + Open Service Broker API):
  - External-domain broker
  - legacy domain broker
  - cdn broker
- Logging stack (BOSH, ELK)
- Prometheus (BOSH)
- Stratos (golang + js)
- uaa-extras (python + OIDC)
- shibboleth (Java, OIDC)

## Compliance items

These are items that are only necessary for someone stepping into a compliance role, but you can still subscribe to the alerts and mailing lists if you're interested:

- [ ] Subscribe to US-CERT alerts: <https://us-cert.cisa.gov/mailing-lists-and-feeds>
- [ ] Subscribe to FedRAMP mailing lists: <https://public.govdelivery.com/accounts/USGSA/subscriber/topics?qsp=USGSA_2224>
- [ ] Read Compliance Lead documents at root of the [Google Drive Security and Compliance](https://drive.google.com/drive/u/0/folders/1_vAXZsdVFYssR1DRCaavBCoDE_uxQCI5) folder
