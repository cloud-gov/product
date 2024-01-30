---
name: Offboard cloud.gov Team Member
title: Checklist for Offboarding a Team Member
about: This is the checklist and requirements for offboarding a team member from the cloud.gov team
labels: ""
assignees: ""
---

# Team Member Offboarding Checklist

## When do we offboard a team member?

We must offboard a team member when they are:

- Absent for 30 or more days, or about to be. For example, team members on detail or extended leave.
- Permanently separating from the team. For example, terminated or reassigned.

See our [AC Policy](https://github.com/cloud-gov/cg-compliance-docs/blob/main/AC-Policy.md), "When a privileged team member has been absent...".

## Special Notes

- **Do not create this issue until the System Owner has formally authorized and requested it.** You can obtain that OK by one of two ways:
  A:

  - [ ] A: System Owner creates this issue

  B:

  - [ ] B.1: System owner emails cloud-gov-compliance@gsa.gov and cloud-gov-operations@gsa.gov with their authorization
  - [ ] B.2: An operator adds links to the email archive of the authorizing email.

- **Please only use first names.**

---

## Instructions

- [ ] Assign this ticket to the person currently staffing the maintenance rotation.

In order to complete `Existing Person`'s exit from the cloud.gov team, the assignee should complete a prescribed set of tasks that will remove any special access.

**Assignee:** The tasks below are organized by the role needed to complete them. If you can’t complete any of the items on your checklist personally, _you are responsible for ensuring that an appropriate person does it_.

For compliance we need to show that critical offboarding actions happen within 24 hours of departure; some actions below **need GitHub issues comments** when completed. Completing tasks _before_ departure is good. (control PS-4: personnel termination).

## `Existing Person`

- [ ] Initiate the process via the [Leaving TTS Handbook page](https://handbook.18f.gov/leaving-tts/)

## Assignee

If the person offboarding is a contractor, reach out to the COR to ensure any offboarding steps specific to their contract are being completed.

- [ ] Remove their access to [StatusPage](https://manage.statuspage.io/organizations/btc69fwyvjh7/team)
- [ ] Remove their agent access to Zendesk - [switch their role to "end user"](https://cloud-gov.zendesk.com/agent/admin/people)
- [ ] Remove them from `@cg-team`, `@cg-operators`, and any other `@cg-` teams in the Slack Team Directory [using the three-dot menu (instructions)](https://get.slack.help/hc/en-us/articles/212906697-User-Groups)
  - Check one of the following:
    - [ ] Temporary federal departure: Remove them all private cloud.gov Slack channels, except `#cg-priv-gov`, so they may continue to receive essential team communications.
    - [ ] Permanent departure: If the person is leaving permanently, they will be removed from all channels automatically.
- [ ] Remove them from the [team roster](https://docs.google.com/spreadsheets/d/187663k5MYJBNlKExLu_nhuovcZQfIbqYCu2n4noNY1o/edit#gid=0)
- [ ] Remove them from the [squad list](https://github.com/cloud-gov/product/blob/main/DeliveryProcess.md#squads)
- [ ] In the [training tracker](https://docs.google.com/spreadsheets/d/1hqU6cNeEB293OT0j3OvbdAFRkrf2zDOrPVxGfnr4sSw/edit#gid=0): if they're staying at TTS, move them to the "former teammates" tab; if they're leaving TTS, delete them from the spreadsheet
- [ ] Remove them as invitees for any meetings on the cloud.gov calendar where they are specifically named
  - Invites where they are listed as part of the `cloud.gov` invitee group will be removed when they are removed from that group by the System Owner
- [ ] Remove them from [our dockerhub org](https://hub.docker.com/orgs/cloudgov)

## System Owner (or person delegated by System Owner)

**The following steps must be conducted and documented within 24 hours of departure**:

- [ ] Exit interview with supervisor (federal employees) or contract account manager / COR (contractors): Discuss with departee the following _information security topics_:
  - They are to remove any non-public cloud.gov data (e.g. keys, passwords, code, documents) from any non-GSA device
  - They are not to disclose any non-public cloud.gov technical practices without authorization from GSA
  - They will not access cloud.gov systems or services without authorization from GSA
  - If the System Owner cannot hold this discussion, they will communicate to GSA OHRM that the above topics need to be communicated to the leaving person.
- [ ] Remove them from the [cloud.gov Github organization](https://github.com/orgs/cloud-gov/people)
- [ ] Remove them from [the cloud.gov team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov/members/active)
- [ ] If they are part of the business unit, remove their access to [GovDelivery](https://admin.govdelivery.com/administrators)

The following do not directly impact cloud.gov security & operations and can happen later:

- [ ] Remove them from [Nessus](https://nessus.fr.cloud.gov/#/settings/users)
- [ ] Remove them from [Tenable (if Compliance Team)](https://community.tenable.com/s/contacts]
- [ ] Remove them from the [Cloud Foundry Community GitHub org cloud.gov team](https://github.com/orgs/cloudfoundry-community/teams/cloud-gov/members)
- [ ] Remove them from [the cloud.gov operations Google Group](https://groups.google.com/a/gsa.gov/forum/#!managemembers/cloud-gov-operations/members/active)
- [ ] Remove them from [the cloud.gov compliance team Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-compliance/members/active)
- [ ] Remove them from [the cloud.gov notifications Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-notifications/members/active)
- [ ] Remove them from [the cloud.gov inquiries Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-inquiries/members/active)
- [ ] Remove them from [the cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-support/members/active)
- [ ] Remove them from [the cloud.gov emergency Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!managemembers/cloud-gov-emergency/members/active)
- [ ] Remove them from [the cloud.gov Federal Employees Google Group](https://groups.google.com/a/gsa.gov/g/cloud-gov-federal-employees/members)
- [ ] Remove them from [our Google Groups for our AWS accounts](https://docs.google.com/document/d/110o1L7EOby3hvE5d-cDhg2LBLHymbZLnMPe9kuk4qp8/edit#) (relevant for PM, Director, and Deputy Director)
- [ ] Remove them from [Ubuntu Advantage](https://ubuntu.com/pro/users)

## Engineering

**The following steps must be conducted and documented within 24 hours of departure**:

- [ ] Not a member of Engineering

-- or --

- [ ] Delete the user in all cloud.gov AWS accounts by submitting a PR to [`aws-admin`](https://github.com/cloud-gov/aws-admin)
- [ ] [Remove their access as an admin](https://cloud.gov/docs/ops/managing-users/#managing-admins) on the platform
- [ ] Remove any privileges that their cloud.gov account has due to membership in the cloud.gov team (even if not in Cloud Ops), such as `admin_ui.user` and `scim.read`
  - [ ] Verify these permissions have been removed using the [cg-scripts validate-admins.sh](https://github.com/18F/cg-scripts/blob/master/validate-admins.sh) run from a jumpbox
- [ ] Remove any Org or Space roles that their cloud.gov account holds due to membership in the cloud.gov team (for example, remove them from the `cloud-gov` and `cloud-gov-operators` organizations)
