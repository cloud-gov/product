# Offboarding Checklist

## Instructions

When someone leaves the cloud.gov team

1. Create a new issue in `cg-product` called "Remove [person's name] from cloud.gov team".
2. View the raw source of this file
3. Copy everything below the line into the new issue's body
4. Replace "LeavingPerson" with the leaving person's name
5. Delete any checklists irrelevant for the skill domain of the leaving person
6. Submit the issue
7. Assign the issue to the person who bravely volunteered to be handle the person's offboarding
8. Put the issue into the "In Progress" pipeline in ZenHub

---

In order to complete LeavingPerson's exit from the cloud.gov team, the assignee should complete a prescribed set of tasks that will remove any special access.

# Directions:
**Assignee:** The tasks below are organized by the role needed to complete them. If you can’t complete any of the items on your checklist personally, _you are responsible for ensuring that an appropriate person does it_.

## Assignee
- [ ] Ask #admins-slack to [remove them](https://get.slack.help/hc/en-us/articles/212906697-User-Groups) from the @cloud-gov-team in the Slack Team Directory
- [ ] Remove them from the [team roster](https://docs.google.com/spreadsheets/d/1mW3tphZ98ExmMxLHPogSpTq8DzYr5Oh8_SHnOTvjRWM/edit#gid=0)
- [ ] Remove them from the [squad list](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md#squads)
- [ ] Remove them from the [training tracker](https://docs.google.com/spreadsheets/d/1hqU6cNeEB293OT0j3OvbdAFRkrf2zDOrPVxGfnr4sSw/edit#gid=0)
- [ ] Remove them as invitees for any meetings on the cloud.gov calendar
- [ ] If they are leaving 18F ensure the [18F Handbook exit process](https://handbook.18f.gov/leaving-18f/#offboarding-process) has been kicked off via the 18F talent team

## System Owner (or person delegated by System Owner)
- [ ] Remove them from [GitHub teams that start with cloud-gov](https://github.com/orgs/18F/teams?utf8=%E2%9C%93&query=cloud-gov)
- [ ] Remove them from the [Cloud Foundry Community GitHub org cloud.gov team](https://github.com/orgs/cloudfoundry-community/teams/cloud-gov)
- [ ] [Remove their access to Zendesk](https://cloud-gov.zendesk.com/agent/admin/people)
- [ ] Remove their access to StatusPage
- [ ] Remove their access to PagerDuty
- [ ] Remove their access to New Relic
- [ ] Remove their access to [Aha!](https://18f.aha.io)
- [ ] Remove them from [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov)
- [ ] Remove them from [the cloud.gov notifications Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-notifications)
- [ ] Remove them from [the cloud.gov inquiries Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-inquiries)
- [ ] Remove them from [the cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-support)
- [ ] Remove them from [the cloud.gov emergency Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-emergency)
- [ ] Remove them from the cg-supportstream private Slack channel
- [ ] Remove them from the project in Float
- [ ] Remove their membership in cloud.gov-specific Trello boards (eg the business-tracker)
- [ ] Remove them from DigitalGov Search access for cg-site
- [ ] Remove them from Nessus


## Cloud Operations
- [ ] Remove them from any IAM roles they hold in AWS E/W and GovCloud
- [ ] [Remove their access as an admin](https://docs.cloud.gov/ops/managing-users/#managing-admins) on the platform
- [ ] Remove any special Org or Space roles that their cloud.gov account holds
- [ ] Confirm the System Owner (or person delegated by System Owner) has removed them from all GitHub teams
- [ ] Ensure any keys they had direct access to are rotated
