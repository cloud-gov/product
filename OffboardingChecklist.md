# Offboarding Checklist

## Instructions

When someone leaves the cloud.gov team

1. Create a new issue called "Remove [person's name] from cloud.gov team".
2. View the raw source of this file
3. Copy everything below the line into the new issue's body
4. Replace "LeavingPerson" with the leaving person's name
5. Submit the issue
6. Assign the issue to the person who bravely volunteered to handle the person's offboarding
7. Put the issue into the "In Progress" pipeline in Jira

---

In order to complete LeavingPerson's exit from the cloud.gov team, the assignee should complete a prescribed set of tasks that will remove any special access.

# Directions:
**Assignee:** The tasks below are organized by the role needed to complete them. If you can’t complete any of the items on your checklist personally, _you are responsible for ensuring that an appropriate person does it_.

## Assignee
- [ ] [Remove them](https://get.slack.help/hc/en-us/articles/212906697-User-Groups) from @cg-team, @cg-operators, and any other @cg- teams in the Slack Team Directory
- [ ] Remove them from the [team roster](https://docs.google.com/spreadsheets/d/1mW3tphZ98ExmMxLHPogSpTq8DzYr5Oh8_SHnOTvjRWM/edit#gid=0)
- [ ] Remove them from the [squad list](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md#squads)
- [ ] In the [training tracker](https://docs.google.com/spreadsheets/d/1hqU6cNeEB293OT0j3OvbdAFRkrf2zDOrPVxGfnr4sSw/edit#gid=0): if they're staying at 18F, move them to the "former teammates" tab; if they're leaving 18F, delete them from the spreadsheet
- [ ] Remove them as invitees for any meetings on the cloud.gov calendar
- [ ] Remove them from the cg-supportstream private Slack channel by asking #admins-slack to remove them
- [ ] If they are leaving 18F, ensure the [18F Handbook exit process](https://handbook.18f.gov/leaving-tts/#offboarding-process) has been kicked off via the 18F talent team
- [ ] [Request](https://cm-jira.usa.gov/projects/JAT/summary) that their Jira account be removed from the cloud.gov team. (If they're leaving the GSA, request that their account be disabled as well.)

## System Owner (or person delegated by System Owner)
- [ ] Remove them from [GitHub teams that start with cloud-gov](https://github.com/orgs/18F/teams?utf8=%E2%9C%93&query=cloud-gov)
- [ ] Remove them from the [Cloud Foundry Community GitHub org cloud.gov team](https://github.com/orgs/cloudfoundry-community/teams/cloud-gov/members)
- [ ] Remove their access to Zendesk - [switch their role to "end user"](https://cloud-gov.zendesk.com/agent/admin/people)
- [ ] Remove their access to [StatusPage](https://manage.statuspage.io/organizations/btc69fwyvjh7/team) - likely have to ask devops@gsa.gov or #infrastructure
- [ ] Remove their access to [PagerDuty](https://18fi.pagerduty.com/users)
- [ ] Remove their access to [New Relic](https://rpm.newrelic.com/accounts/907948)
- [ ] Remove them from [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov/members/active)
- [ ] Remove them from [the cloud.gov notifications Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-notifications/members/active)
- [ ] Remove them from [the cloud.gov inquiries Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-inquiries/members/active)
- [ ] Remove them from [the cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-support/members/active)
- [ ] Remove them from [the cloud.gov emergency Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-emergency/members/active)
- [ ] Remove them from [the cloud.gov operations Google Group](https://groups.google.com/a/gsa.gov/forum/#!managemembers/cloud-gov-operations/members/active)
- [ ] Remove them from [Search.gov](https://search.gov/) access for cg-site
- [ ] Remove them from [Nessus](https://nessus.fr.cloud.gov/#/settings/users)

## Cloud Operations
- [ ] Delete the user in all cloud.gov AWS accounts.  There should be info on which AWS accounts you need to look at [here](https://docs.google.com/document/d/110o1L7EOby3hvE5d-cDhg2LBLHymbZLnMPe9kuk4qp8/edit)
- [ ] Remove them from our Google Cloud Platform (GCP) Projects (by asking Derrick Rogers in GSA IT)
- [ ] Remove them from [the cloud.gov group](https://app.cloudcheckr.com/Admin/UserGroupBuilder/fb111fab-ef5d-48d0-9472-cff691e1bd9c) in CloudCheckr.
- [ ] [Remove their access as an admin](https://cloud.gov/docs/ops/managing-users/#managing-admins) on the platform
- [ ] Remove any privileges that their cloud.gov account has due to membership in the cloud.gov team (even if not in Cloud Ops), such as `admin_ui.user` and `scim.read`
- [ ] Remove any Org or Space roles that their cloud.gov account holds due to membership in the cloud.gov team (for example, remove them from the `cloud-gov` and `cloud-gov-operators` organizations)
- [ ] Confirm the System Owner (or person delegated by System Owner) has removed them from all GitHub teams
- [ ] Ask #infrastructure to remove them from [the cloudgov subteam in Docker Hub|https://hub.docker.com/u/18fgsa/dashboard/teams/?team=cloudgov].

- [ ] Ensure any keys or passwords they had direct access to are rotated
