# Offboarding Checklist

## Instructions

When someone leaves the cloud.gov team

1. Create a new issue in the private team repo called "Remove [person's name]".
2. View the raw source of this file
3. Copy everything below the line into the new issue's body
4. Replace "LeavingPerson" with the leaving person's name
5. Submit the issue
6. Assign the issue to the person who bravely volunteered to handle the person's offboarding
7. Put the issue into the "Blocked" column [on our project board](https://github.com/orgs/cloud-gov/projects/2)

---

In order to complete [NAME]'s exit from the cloud.gov team, the assignee should complete a prescribed set of tasks that will remove any special access.

# Directions:

**Assignee:** The tasks below are organized by the role needed to complete them. If you can’t complete any of the items on your checklist personally, _you are responsible for ensuring that an appropriate person does it_.

For compliance we need to show that critical offboarding actions happen within 24 hours of departure; some actions below **need GitHub issues comments** when completed. Completing tasks _before_ departure is good. (control PS-4: personnel termination)

## [NAME]

- [ ] Initiate the process via the [Leaving TTS Handbook page](https://handbook.18f.gov/leaving-tts/)

## Assignee

If the person offboarding is a contractor follow the steps in the [offboarding checklist](https://docs.google.com/spreadsheets/d/1u5GQ2i4u20x3r1ryXifWf99ZM_U6BPOu-rHaoFADZ6k/edit#gid=1078790596)t in addition to the following steps below.

- [ ] Mention the TTS HR liaison and TTS Tech Portfolio in this ticket so they can update with their status
  - As part of TTS offboarding, TTS Tech Portfolio will automatically:
  - Remove their access to [StatusPage](https://manage.statuspage.io/organizations/btc69fwyvjh7/team) 
  - Remove them from [the cloudgov subteam in Docker Hub](https://hub.docker.com/u/18fgsa/dashboard/teams/?team=cloudgov)
  - Remove write/push access for NPM from [cloudgov-style](https://www.npmjs.com/package/cloudgov-style)
  - Remove them from [HackerOne](https://hackerone.com/)
  - If they are leaving GSA, ask `#admins-slack` to convert them to a single-channel alumni user
  - Remove their agent access to Zendesk - [switch their role to "end user"](https://cloud-gov.zendesk.com/agent/admin/people)
  - Remove them from [the cloud.gov group](https://app.cloudcheckr.com/Admin/UserGroupBuilder/fb111fab-ef5d-48d0-9472-cff691e1bd9c) in CloudCheckr
  - Update this issue with a comment within 24h of departure that the above steps are complete
- [ ] Remove them from `@cg-team`, `@cg-operators`, and any other `@cg-` teams in the Slack Team Directory [using the three-dot menu (instructions)](https://get.slack.help/hc/en-us/articles/212906697-User-Groups)
- [ ] Remove them from the [team roster](https://docs.google.com/spreadsheets/d/1mW3tphZ98ExmMxLHPogSpTq8DzYr5Oh8_SHnOTvjRWM/edit#gid=0)
- [ ] Remove them from the [squad list](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md#squads)
- [ ] In the [training tracker](https://docs.google.com/spreadsheets/d/1hqU6cNeEB293OT0j3OvbdAFRkrf2zDOrPVxGfnr4sSw/edit#gid=0): if they're staying at TTS, move them to the "former teammates" tab; if they're leaving TTS, delete them from the spreadsheet
- [ ] Remove them as invitees for any meetings on the cloud.gov calendar where they are specifically named
    - Invites where they are listed as part of the `cloud.gov` invitee group will be removed when they are removed from that group by the System Owner

## System Owner (or person delegated by System Owner)

**The following steps must be conducted and documented within 24 hours of departure**:

- [ ] Exit interview with supervisor or contract account manager: Discuss with departee the following _information security topics_:
  - They are to remove any non-public cloud.gov data (e.g. keys, passwords, code, documents) from any non-GSA device
  - They are not to disclose any non-public cloud.gov technical practices without authorization from GSA
  - They will not access cloud.gov systems or services without authorization from GSA
  - If the System Owner cannot hold this discussion, they will communicate to GSA OHRM that the above topics need to be communicated to the leaving person.
- [ ] Remove them from the [cloud.gov Github organization](https://github.com/orgs/cloud-gov/people)
- [ ] Remove them from [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov/members/active)
- [ ] If they are part of the business unit, remove their access to [GovDelivery](https://admin.govdelivery.com/administrators)

The following do not directly impact cloud.gov security & operations and can happen later:

- [ ] Remove them from [Nessus](https://nessus.fr.cloud.gov/#/settings/users)
- [ ] Remove them from the [Cloud Foundry Community GitHub org cloud.gov team](https://github.com/orgs/cloudfoundry-community/teams/cloud-gov/members)
- [ ] Remove them from the `CG-PRIV` Google Group
- [ ] Remove them from [the cloud.gov operations Google Group](https://groups.google.com/a/gsa.gov/forum/#!managemembers/cloud-gov-operations/members/active)
- [ ] Remove them from [the cloud.gov compliance team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-compliance/members/active)
- [ ] Remove them from [the cloud.gov notifications Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-notifications/members/active)
- [ ] Remove them from [the cloud.gov inquiries Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-inquiries/members/active)
- [ ] Remove them from [the cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-support/members/active)
- [ ] Remove them from [the cloud.gov emergency Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-emergency/members/active)
- [ ] Remove them from [our Google Groups for our AWS accounts](https://docs.google.com/document/d/110o1L7EOby3hvE5d-cDhg2LBLHymbZLnMPe9kuk4qp8/edit#) (relevant for PM, Director, and Deputy Director)
- [ ] Remove them from [Search.gov](https://search.gov/) access for cg-site by pinging the search.gov team in the #search Slack channel

## Cloud Operations

**The following steps must be conducted and documented within 24 hours of departure**:

- [ ] Delete the user in all cloud.gov AWS accounts.  There should be info on which AWS accounts you need to look at [here](https://docs.google.com/document/d/110o1L7EOby3hvE5d-cDhg2LBLHymbZLnMPe9kuk4qp8/edit)
- [ ] [Remove their access as an admin](https://cloud.gov/docs/ops/managing-users/#managing-admins) on the platform
- [ ] Remove any privileges that their cloud.gov account has due to membership in the cloud.gov team (even if not in Cloud Ops), such as `admin_ui.user` and `scim.read`
    - [ ] Verify these permissions have been removed using the [cg-scripts validate-admins.sh](https://github.com/18F/cg-scripts/blob/master/validate-admins.sh) run from a jumpbox
- [ ] Remove any Org or Space roles that their cloud.gov account holds due to membership in the cloud.gov team (for example, remove them from the `cloud-gov` and `cloud-gov-operators` organizations)
- [ ] Ensure any keys or passwords they had direct access to are rotated
