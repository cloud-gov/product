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
**Buddy:** If you can’t complete any of the items on your checklist personally, _you are responsible for ensuring that someone with the correct access completes that item_.

## New Person checklist

### Getting to know cloud.gov
- [ ] Take judicious notes on what about this onboarding process or cloud.gov is confusing or frustrating. If you notice a problem (especially with things like documentation), you are more than welcome to fix it! At the very least, please share this information with your buddy (or someone) at some point so we can make the team/platform better. (You can also file issues and pull requests on [the template for Onboarding issues](https://github.com/18F/cg-product/blob/master/OnboardingChecklist.md).)
- [ ] Bookmark the [pertinent links listed here](https://github.com/18F/cg-product/blob/master/PertinentLinks.md).
- [ ] Figure out who your onboarding buddy is (they should reach out to you) and make sure this issue is assigned to them
- [ ] Read the documents and links in the "cloud.gov" section of the [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md)
- [ ] Try to [deploy a sample application to cloud.gov](https://docs.cloud.gov/getting-started/your-first-deploy/) to get familiar with the basics of the PaaS from a user's perspective
- [ ] Install the [ZenHub](https://zenhub.io) browser extension to enable you to see kanban boards, hierarchical issues, and burndown charts in GitHub
- [ ] Join [the cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-support), so you can see how we handle non-18F support and get visibility of technical discussions happening with outside groups
- [ ] Join [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov), so you can participate in team-wide internal communication
- [ ] Consider joining [Cloud Foundry's Slack channels] (https://slack.cloudfoundry.org/) (we sometimes talk to folks in #gov and #gov-private – you'll need a team member to invite you to the latter)
- [ ] Figure out what themes you're likely to work in, and complete the checklist below that relates to it
- [ ] Once you've finished the remaining checklists below, make suggestions for steps that would have improved your onboarding experience as pull requests on [the onboarding checklist template](https://github.com/18F/cg-product/blob/master/OnboardingChecklist.md) used to make this issue

### Required items for all team members

These items help us fulfill security and compliance requirements (including for FedRAMP). If you get stuck, or if these requirements are confusing, ask for help from your buddy or in a cloud.gov channel.

- [ ] Read the documents and links in the "required" section of the [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md)
- [ ] Coordinate with your onboarding buddy to go through Incident Response Training within 60 days of joining the team (and annually after that).
- [ ] Coordinate with your onboarding buddy to go through Contingency Planning training within 10 days if you'll be taking on a significant role in our Contingency Planning processes (or annually if not).
- [ ] Subscribe to [the cloud.gov team calendar](https://calendar.google.com/calendar/embed?src=gsa.gov_0samf7guodi7o2jhdp0ec99aks@group.calendar.google.com&ctz=America/Los_Angeles) (click the + in the bottom right) so you know when assorted team meetings are happening in the various streams
- [ ] Subscribe (through the GitHub watch function) to the [cg-site](https://github.com/18F/cg-site) GitHub repository notifications

### Theme-specific items

For explanations of our theme names, see [this glossary](https://github.com/18F/cg-product#sub-teamsthemes-of-work).

#### Atlas-specific items

- [ ] Read the documents and links in the "Cloud Operations" section of the [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md)
- [ ] Bookmark [the Atlas kanban board view](https://github.com/18F/cg-product#boards?labels=Atlas&showPRs=false)
- [ ] Join the #cloud-gov-atlas channel on Slack
- [ ] [Set up Cloud Foundry locally](https://docs.cloud.gov/ops/creating-a-local-dev-environment-in-Virtual-Box/) and push an app to it
- [ ] Join [the Cloud Foundry Slack](http://slack.cloudfoundry.org/)

#### Agent Q-specific items
- [ ] Read the documents and links in the "Cloud Operations" section of the [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md)
- [ ] Bookmark [the Atlas kanban board view](https://github.com/18F/cg-product#boards?labels=Atlas&showPRs=false)
- [ ] Bookmark [the Agent Q kanban board view](https://github.com/18F/cg-product#boards?labels=AgentQ&showPRs=false)
- [ ] Join the #cloud-gov-agent-q channel on Slack
- [ ] Join [the Cloud Foundry Slack](http://slack.cloudfoundry.org/)

#### Navigator-specific items

- [ ] Read the documents and links in the "Navigator" section of the [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md)
- [ ] Bookmark [the Atlas kanban board view](https://github.com/18F/cg-product#boards?labels=Atlas&showPRs=false)
- [ ] Join the `#cloud-gov-navigator` channel on Slack
- [ ] Ping @standup-bot for instructions on front end channel standup
- [ ] Bookmark link to [design folder](https://drive.google.com/drive/u/1/folders/0BwLqM4Nicmq-bUt0NjRjclFMUEU)
- [ ] [Request access to 18F Google Analytics](https://handbook.18f.gov/google-analytics/), so you can view cloud.gov site analytics ([including for the dashboard](https://docs.google.com/document/d/1gSbP2ak2a3QLpCZIF_KlbQ2QHE6RjDI-7ZnnrJZvMDE/edit))
- [ ] Ask for an invite to a DigitalGov Search account for cg-docs, so you can configure it and view analytics

##### If developing
- [ ] Set up the [landing/docs page](https://github.com/18F/cg-site), [dashboard](https://github.com/18F/cg-dashboard), and [cg-style](https://github.com/18F/cg-style) locally
- [ ] Set up cg-style to be [linked to the other sites locally](https://github.com/18F/cg-style#development-and-contributing-setup)
- [ ] Have cloud.gov person send the cg-dashboard testing env vars through Fugacious

#### HighBar-specific items
- [ ] Read the documents and links in the "Highbar" section of the [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md)
- [ ] Bookmark [the HighBar kanban board view](https://github.com/18F/cg-product#boards?labels=HighBar&showPRs=false)
- [ ] Make sure you join the #cloud-gov-highbar channel on Slack

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

- [ ] Help them review and understand the responsibilities of becoming a Cloud Operations team member, as outlined in our SSP. (See [reading list](https://github.com/18F/cg-product/blob/master/ReadingList.md) -- specific sections to come).
- [ ] Grant all appropriate access as outlined in the [Atlas/AgentQ access list](https://github.com/18F/cg-product/blob/masterAccessList.md). 
- [ ] Give them a walkthrough of cloud.gov from an architecture and repository perspective.
   - Illustrate the relationship between external repos and our `cg-deploy` repositories.
   - Walk them through the basics of working with Cloud Foundry, BOSH and Concourse/fly as the team does on a daily basis.
- [ ] Solicit and answer any and all questions.
