# Onboarding Checklist

## Instructions

When someone new joins the cloud.gov team:

1. Create a new issue in `cg-product` called "Ramp up [person's name] on cloud.gov team".
2. View the raw source of this file
3. Copy everything below the line into the new issue's body
4. Replace "NewPerson" with the new person's name
5. Replace "Buddy" with the onboarding buddy's name
4. Delete any checklists irrelevant for the new person's skill domain (theme)
5. Submit the issue
6. Assign the issue to the person who bravely volunteered to be the new person's Onboarding Buddy
7. Put the issue into the "In Progress" pipeline in ZenHub

---

In order to get NewPerson productively contributing to the cloud.gov team, Buddy should help NewPerson complete a prescribed set of tasks that will bring them up to speed.

# Directions:
**NewPerson and Buddy:** Try to go through your checklists in order.
**Buddy:** If you can’t complete any of the items on your checklist personally, _you are responsible for ensuring that an appropriate person does it_.

## New Person checklist

### Getting to know cloud.gov
- [ ] Take judicious notes on what about this onboarding process or cloud.gov is confusing or frustrating. If you notice a problem (especially with things like documentation), you are more than welcome to fix it! At the very least, please share this information with your buddy (or someone) at some point so we can make the team/platform better. (You can also file issues and pull requests on [the template for Onboarding issues](https://github.com/18F/cg-product/blob/master/OnboardingChecklist.md).)
- [ ] Bookmark the [pertinent links listed here](./PertinentLinks.md).
- [ ] Figure out who your onboarding buddy is (they should reach out to you) and make sure this issue is assigned to them
- [ ] Read [the team onboarding document](https://github.com/18F/cg-product/blob/master/Onboarding.md) for more context about cloud.gov
- [ ] Read the ["What is it?"](https://docs.google.com/presentation/d/1nCcti3dXG9TVGW3OqaWtnf96oXX8U8SBTM_WePFO_dg/edit#slide=id.p) presentation for a rundown of what cloud.gov is and does
- [ ] Read through [the Introduction section of docs.cloud.gov](https://docs.cloud.gov/) for a broader understanding of cloud.gov, especially as we present it to potential customers/users
- [ ] Read the [January 2016 cloud.gov "Executive Business Case" document](https://docs.google.com/document/d/138OcG0Lt6gr9J0wM0TzzPNyTROmYAwfLIDujtweiwGw/edit#) for greater context about cloud.gov's potential impact in government
- [ ] Try to [deploy a sample application to cloud.gov](https://docs.cloud.gov/getting-started/your-first-deploy/) to get familiar with the basics of the PaaS from a user's perspective
- [ ] Check out the [roadmap](https://18f.aha.io/products/CGP/feature_cards) to get a high-level view of recently-completed, in-progress, and upcoming features
- [ ] Install the [ZenHub](https://zenhub.io) browser extension to enable you to see kanban boards, hierarchical issues, and burndown charts in GitHub
- [ ] Read the [Delivery Process document](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md) to learn about how we work
- [ ] Join [the cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-support), so you can see how we handle non-18F support and get visibility of technical discussions happening with outside groups
- [ ] Join [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov), so you can participate in team-wide internal communication
- [ ] Figure out what themes you're likely to work in, and complete the checklist below that relates to it
- [ ] Once you've finished the remaining checklists below, make suggestions for steps that would have improved your onboarding experience as pull requests on [the onboarding checklist template](https://github.com/18F/cg-product/blob/master/OnboardingChecklist.md) used to make this issue

### Required items for all team members

These items help us fulfill security and compliance requirements (including for FedRAMP). If you get stuck, or if these requirements are confusing, ask for help from your buddy or in a cloud.gov channel.

- [ ] Read the [18F Security Policies and Procedures](https://github.com/18F/compliance-docs). These documents (which are mostly quite short) explain the high-level policies and procedures we must comply with while running cloud.gov.
- [ ] Read the [Incident Response Guide](https://docs.cloud.gov/ops/security-ir/).
- [ ] Coordinate with your onboarding buddy to go through Incident Response Training within 60 days of joining the team (and annually after that).
- [ ] Read the [Contingency Plan](https://docs.cloud.gov/ops/contingency-plan/).
- [ ] Read the [Continuous Monitoring Plan](https://drive.google.com/file/d/0B1cewEqKcWCbZlFuQklZVWpLV1k/view), particularly section 2.5.
- [ ] Coordinate with your onboarding buddy to go through Contingency Planning training within 10 days if you'll be taking on a significant role in our Contingency Planning processes (or annually if not).
- [ ] Read the [Configuration Management Plan](https://docs.cloud.gov/ops/configuration-management/).
- [ ] Subscribe to [the cloud.gov team calendar](https://calendar.google.com/calendar/embed?src=gsa.gov_0samf7guodi7o2jhdp0ec99aks@group.calendar.google.com&ctz=America/Los_Angeles) (click the + in the bottom right) so you know when assorted team meetings are happening in the various streams
- [ ] Subscribe to the [cg-docs](https://github.com/18F/cg-docs) GitHub repository notifications

### Theme-specific items

For explanations of our theme names, see [this glossary](https://github.com/18F/cg-product#sub-teamsthemes-of-work).

#### Atlas-specific items

- [ ] Bookmark [the Atlas kanban board view](https://github.com/18F/cg-product#boards?labels=Atlas&showPRs=false)
- [ ] Join the #cloud-gov-atlas channel on Slack
- [ ] Watch [Build Your Own Private Cloud Foundry](https://www.youtube.com/watch?v=v85r4Hy3jbs) to learn about running Cloud Foundry
- [ ] [Set up Cloud Foundry locally](https://docs.cloud.gov/ops/creating-a-local-dev-environment-in-Virtual-Box/) and push an app to it
- [ ] Learn about [BOSH](http://bosh.io/): watch [this video](https://www.youtube.com/watch?v=2jpN1mSPZ4Q) and see [our manifests](https://github.com/18F/cg-manifests) (and read [this](http://events.linuxfoundation.org/sites/events/files/slides/seven-stages-of-bosh.pdf) for levity)
- [ ] Get to know how UAA is deployed/integrated
- [ ] Get familiar with [Terraform](https://www.terraform.io/) by going through the [getting started guide](https://www.terraform.io/intro/getting-started/install.html)
- [ ] Learn about [Concourse](https://concourse.ci/) and try a [tutorial](https://github.com/starkandwayne/concourse-tutorial)
- [ ] Check out our [staging](https://ci-stage.cloud.gov/) and [production](https://ci.cloud.gov) Concourse instances, and take a look at some of [our pipelines](https://github.com/18F?utf8=%E2%9C%93&query=cg-deploy)
- [ ] Join [the Cloud Foundry Slack](http://slack.cloudfoundry.org/)
- [ ] Get familiar with our AWS setup

#### Agent Q-specific items
- [ ] Bookmark [the Agent Q kanban board view](https://github.com/18F/cg-product#boards?labels=AgentQ&showPRs=false)
- [ ] Join the #cloud-gov-agent-q channel on Slack
- [ ] Read about Cloud Foundry [services from a user perspective](http://docs.cloudfoundry.org/devguide/services/)
- [ ] Read about [implementing services](http://docs.cloudfoundry.org/services/)
- [ ] Take a look at [our existing brokers](https://github.com/18F?utf8=%E2%9C%93&query=broker)
- [ ] Learn about [Concourse](https://concourse.ci/): check out our [staging](https://ci-stage.cloud.gov/) and [production](https://ci.cloud.gov) instances, and take a look at some of [our pipelines](https://github.com/18F?utf8=%E2%9C%93&query=cg-deploy)
- [ ] Join [the Cloud Foundry Slack](http://slack.cloudfoundry.org/)

#### Navigator-specific items

- [ ] Join the `#cloud-gov-navigator` channel on Slack
- [ ] Ping @standup-bot for instructions on front end channel standup
- [ ] Review the main [front end board](https://github.com/18F/cg-dashboard/pulls#boards?repos=55727091,39210774,49169967,40567233&labels=Navigator&showPRs=false) (ensure to filter by the "Navigator" label)
- [ ] Bookmark link to [design folder](https://drive.google.com/drive/u/1/folders/0BwLqM4Nicmq-bUt0NjRjclFMUEU)
- [ ] Review the primary cloud.gov sites: [the dashboard](https://dashboard.cloud.gov/#/), [main landing page](https://cloud.gov/), and [documentation](https://docs.cloud.gov/).
- [ ] [Request access to 18F Google Analytics](https://handbook.18f.gov/google-analytics/), so you can view cloud.gov site analytics ([including for the dashboard](https://docs.google.com/document/d/1gSbP2ak2a3QLpCZIF_KlbQ2QHE6RjDI-7ZnnrJZvMDE/edit))
- [ ] Ask for an invite to a DigitalGov Search account for cg-docs, so you can configure it and view analytics

##### If developing
- [ ] Set up the [landing page](https://github.com/18F/cg-landing), [dashboard](https://github.com/18F/cg-dashboard), [docs](https://github.com/18F/cg-docs), and [cg-style](https://github.com/18F/cg-style) locally
- [ ] Set up cg-style to be [linked to the other sites locally](https://github.com/18F/cg-style#development-and-contributing-setup)
- [ ] Have cloud.gov person send the cg-dashboard testing env vars through Fugacious
- [ ] Review [dashboard contributing guide](https://github.com/18F/cg-dashboard/blob/master/CONTRIBUTING.md) and [cg-style standards](https://github.com/18F/cg-style/blob/master/documentation/frontend_standards.md)

##### For review
- Review the [design principles wiki](https://github.com/18F/cg-product/wiki) which explains the thinking behind the product and where that thinking comes from
- Review the [design resource request document](https://docs.google.com/document/d/1s96VP6PB7fbc8g_GwgAZ1hCPmew-J35ZOJx772c1AZ4/edit) if you haven’t already to get a sense of your role on the project
- Review the [design principles doc](https://docs.google.com/spreadsheets/d/14Y3RKaLUt6RPX5w13iz7oaSCpojEQ-Wqjnd8Ie_VkCc/edit#gid=259774738) to get a sense of how the cloud.gov team feels about the product
- Review the [competitive analysis](https://docs.google.com/spreadsheets/u/1/d/194tGz75NFwFyH8jT7zY_n-O0I7N4yAGYtIG4hw9qPcQ/edit?usp=drive_web) to get a sense of our "competitors" and their dashboards.
- Review the [cg-style styleguide](https://pages.18f.gov/cg-style/) to get a sense of the global cloud.gov visual style.
- Review the [US Web Design Standards](https://standards.usa.gov/) as cg-style was built from it.
- Review the dashboard: current [prod](https://dashboard.cloud.gov/#/), [master](https://dashboard-master.apps.cloud.gov/#/) and [staging](https://dashboard-staging.apps.cloud.gov/#/)
- Review the Cloud Foundry [community UI](http://ui.apps.cloud.gov/), a UI that members of the Cloud Foundry community created and that we're using a basis for our own dashboard design

#### HighBar-specific items
- [ ] Bookmark [the HighBar kanban board view](https://github.com/18F/cg-product#boards?labels=HighBar&showPRs=false)
- [ ] Make sure you join the #cloud-gov-highbar channel on Slack
- [ ] Read through the description of [Compliance Toolkit](https://github.com/18F/compliance-toolkit/#readme)
- [ ] Watch [Handling FISMA Faster and Better](https://www.youtube.com/watch?v=T1S52B1-NT4) for important context and background on the federal regulatory context in which cloud.gov operates.
- [ ] Do a cursory read of [Before You Ship](https://pages.18f.gov/before-you-ship/)
- [ ] Read [the intro to Compliance Masonry](https://github.com/opencontrol/compliance-masonry#readme)

---
## Buddy checklist
- [ ] Introduce yourself to the new team member and give them some of your background so they know who you are
- [ ] Identify a straightforward, well-groomed story in progress that involves their skills domain, schedule a meeting with the owner for an introduction (if it's not you), and setup pairing sessions several times in the first week on the project.
- [ ] Identify a straightforward, well-groomed first story, ideally something they could conceivably complete in their first two/three weeks using their existing skills. Discuss the context with them, then make them the assignee for the card.
- [ ] Make suggestions for how the onboarding experience could have been improved as PRs on [the onboarding template](https://github.com/18F/cg-product/blob/master/OnboardingChecklist.md).

### Required items for all team members

These items help us fulfill security and compliance requirements (including for FedRAMP).

- [ ] Make sure they're in [the list of people working on the project](https://docs.google.com/spreadsheets/d/1mW3tphZ98ExmMxLHPogSpTq8DzYr5Oh8_SHnOTvjRWM/edit#gid=0)
- [ ] Add them to the @cloud-gov-team [in Slack’s Team Directory](https://get.slack.help/hc/en-us/articles/212906697-User-Groups#edit-a-user-group), which also adds them to the right channels (or ask #admins-slack if you don't have permission to do this)
- [ ] Add them to the recurring cloud.gov meetings that are relevant for them in [the team calendar](https://calendar.google.com/calendar/embed?src=gsa.gov_0samf7guodi7o2jhdp0ec99aks@group.calendar.google.com&ctz=America/Los_Angeles)
- [ ] Ask `#admins-github` to add them to the [@18F/cloud.gov team](https://github.com/orgs/18F/teams/cloud-gov) on GitHub

### Atlas-specific required items

- [ ] Help them review and understand the responsibilities of becoming a Cloud Operations team member, as listed in our SSP
- [ ] Ask `#admins-github` to have them added to the [@18F/cloud-gov-ops](https://github.com/orgs/18F/teams/cloud-gov-ops) team on GitHub **(For contractors: Confirm they have cleared GSA security review before doing this one!)**
- [ ] If the new person is a contractor, ask `#admins-github` to have them added to the [@18F/cloud-gov-contractors](https://github.com/orgs/18F/teams/cloud-gov-contractors) team on GitHub
- [ ] Grant them access to the following: AWS GovCloud, Nessus Manager GUI, New Relic, PagerDuty, StatusPage
- [ ] [Make them an admin](https://docs.cloud.gov/ops/managing-users/#managing-admins) of the platform
- [ ] Take them through [AWS onboarding](https://docs.cloud.gov/ops/aws-onboarding/)
- [ ] Give them a walkthrough of cloud.gov from an architecture and repository perspective
