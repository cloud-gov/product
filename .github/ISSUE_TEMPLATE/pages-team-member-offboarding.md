 #### User Story

 ## Special Notes

- **Do not create this issue until the System Owner has formally authorized and requested it.**
- **Please only use first names.**

---

Offboard <Person>

#### Acceptance Criteria

- [ ] Create offboarding issue in GitHub
- [ ] Remove any access to Federalist backend in cloud.gov (Space Dev in Staging)
- [ ] Remove from #federalist- channels in Slack as needed, and remove from @federalist-team Slack user group
- [ ] Remove from #cg-* private channels in Slack as needed
- [ ] Remove from daily standup, retro, and sprint planning
- [ ] Remove from cloud-gov-team in cloud-gov Github org.
- [ ] Remove from backups list if appropriate.

When a pages ops team member leaves the team:
- [ ] Remove access to Federalist backend org (gsa-18f-federalist) and production spaces ( production, sites, redirects) in cloud.gov.
- [ ] Remove team member from Statuspage
- [ ] This step is moot if the employee is leaving GSA since their 2FA will be disabled, but is still good hygiene.
- [ ] Remove from federalist-admins and federalist-contributor in 18F GitHub org.
- [ ] Remove user from Federalist Github project
- [ ] Remove from pages-ops in cloud-gov Github org.
- [ ] Remove from federalist-users Github org.
- [ ] Remove from @federalist-operators Slack user group
- [ ] Remove from daily standup, retro, sprint planning
- [ ] Remove from any email alerting policies within the New Relic account.
- [ ] Remove from federalist-support, federalist-alerts, and federalist-inquiries Google Groups
- [ ] Remove from https://federalist-support.zendesk.com/agent by requesting the user removal from a Zendesk owner
- [ ] Remove from backups list if appropriate.
- [ ] Have a cloud.gov operator remove the user from the “pages.admin” group in the cloud.gov UAA by using the make-pages-admin.sh script
- [ ] Have a cloud.gov operator remove the user from “concourse.pages” team in the cloud.gov OpsUAA by using the make-pages-ops-admin.sh script so they cannot access Concourse CI

