---
name: Offboard Existing cloud.gov Pages Team Member
title: Checklist for Offboarding an Existing Pages Team member
about: This is the checklist and requirements for offboarding an existing Pages team member
labels: ''
assignees: ''
---

 # Offboard cloud.gov Pages Team Member

 ## Special Notes

- **Do not create this issue until the System Owner has formally authorized and requested it.** You can obtain that OK by one of two ways:
  A:
  - [ ] A: System Owner creates this issue

  B:
  - [ ] B.1: System owner emails cloud-gov-compliance@gsa.gov and cloud-gov-pages-operations@gsa.gov with their authorization
  - [ ] B.2: An operator adds links to the email archive of the authorizing email.
**Please only use first names.**

---

Offboard <Person>

#### Acceptance Criteria

- [ ] Create offboarding issue in GitHub
- [ ] Remove any access to Federalist backend in cloud.gov (Space Dev in Staging)
- [ ] Remove from #cg-pages- channels in Slack as needed, and remove from @cg-pages-team Slack user group
- [ ] Remove from #cg-* private channels in Slack as needed
- [ ] Remove from daily standup, retro, and sprint planning
- [ ] Remove from cloud-gov-team in cloud-gov Github org.
- [ ] Remove from backups list if appropriate.

When a pages ops team member leaves the team:
- [ ] Remove access to Federalist backend org (gsa-18f-federalist) and production spaces ( production, sites, redirects) in cloud.gov.
- [ ] Remove team member from Statuspage
- [ ] This step is moot if the employee is leaving GSA since their 2FA will be disabled, but is still good hygiene.
- [ ] Remove from pages-ops in cloud-gov Github org.
- [ ] Remove from @cg-pages-team  Slack user group
- [ ] Remove from daily standup, retro, sprint planning
- [ ] Remove from any email alerting policies within the New Relic account.
- [ ] Remove from pages-support and pages-operations Google Groups
- [ ] Remove from https://pages-support.zendesk.com/agent by requesting the user removal from a Zendesk owner
- [ ] Remove from backups list if appropriate.
- [ ] Have a cloud.gov operator remove the user from the “pages.admin” group in the cloud.gov UAA by using the make-pages-admin.sh script
- [ ] Have a cloud.gov operator remove the user from “concourse.pages” team in the cloud.gov OpsUAA by using the make-pages-ops-admin.sh script so they cannot access Concourse CI

