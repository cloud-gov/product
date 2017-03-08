# Continuous Monitoring Checklist

## Instructions

After delivery of a monthly ConMon report:

1. Create a new issue in the cloud.gov task tracker called "Deliver ConMon report for [due date]". Our standard due date is the 2nd of the month. If that date falls on a weekend or federal holiday, the due date is the last business day before the 2nd.
1. Categorize it as "Ready", in the Highbar theme of work, and in the FedRAMP-related-work category for that quarter.
1. Copy everything below the line into the issue, with checklists for the checklist items.
1. Replace [due date] in title and body with the next due date.

---

In order for us to update the JAB on our compliance in a consistent way, we need to deliver a Continuous Monitoring report on [due date]. We should run the scans on approximately the same day of each month (adjusted for weekends and federal holidays) - approximately the 23rd. For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary).

**Acceptance criteria - by COB on [1 work day before the due date], we've done the following**
-  [ ] Uploaded our ConMon POA&M to https://community.max.gov/pages/viewpage.action?pageId=1034682621
-  [ ] Uploaded our web scans to https://community.max.gov/display/FedRAMPExternal/GSA+18F+Cloud.gov+Web+Scans
-  [ ] Uploaded our OS scans to https://community.max.gov/pages/viewpage.action?pageId=1034682662
-  [ ] Uploaded our database (RDS) scans to https://community.max.gov/pages/viewpage.action?pageId=1034682662
-  [ ] Uploaded any deviation request forms to https://community.max.gov/display/FedRAMPExternal/GSA+18F+Cloud.gov+Submitted+Deviation+Requests
-  [ ] Emailed relevant FedRAMP team members to let them know that's done

**As soon as possible after filing this issue**

- [ ] We've scheduled a 15 min meeting for some reasonable date a few days before the 23rd, inviting anyone on the cloud.gov who is involved in compliance work this month (including at least one Cloud Operations person).
- [ ] We've put an item on the cloud.gov calendar for the business day before the due date ("ConMon report due by COB [FedRAMP]"), as a reminder to ourselves.

**At that meeting**

- [ ] We had a 15 min meeting to go over the checklist, assign sub-tasks (label each task with the name of the person assigned to it), and adjust the checklist as necessary. When possible, assign a pair of people for each scanning task so that more of us learn how to grab these.

**On approximately the 23rd of the month**

- [ ] We ran OWASP ZAP on the following domains using steps #1-6 of the manual scanning instructions at https://pages.18f.gov/before-you-ship/security/dynamic-scanning/#manual-scanning - authenticated, passive: https://ci.fr.cloud.gov/ (requires Cloud Ops auth), https://community.fr.cloud.gov/, https://dashboard.fr.cloud.gov/, https://account.fr.cloud.gov/, https://landing.app.cloud.gov/, https://login.fr.cloud.gov/, https://opslogin.fr.cloud.gov/login, https://logs.fr.cloud.gov/, https://metrics.fr.cloud.gov/ (requires Cloud Ops auth). You have to log in so that ZAP can scan inside the authenticated website. Make sure to scan _only_ those sites, rather than browsing other URLs while ZAP is running, to prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report).
- [ ] We exported and uploaded those fresh OWASP ZAP results in XML format to a folder in the folder at https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U - you can upload one XML file with results from all the sites, or upload a series of separate XML files with results per site.
- [ ] We also grabbed the OWASP ZAP "context" export with settings info and uploaded it to that folder.
- [ ] We also grabbed the OWASP ZAP scans in human-readable HTML format and uploaded them to that folder.
- [ ] We grabbed a fresh set of Nessus scans (both OS and database/RDS) from https://nessus.fr.cloud.gov/ in .nessus format and uploaded the fresh results to a folder in the folder at https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U - requires auth (Cloud Ops or Deputy Director).
- [ ] We also grabbed the Nessus HTML export - https://docs.tenable.com/nessus/6_8/Content/Exported_Results.htm - for those scans and uploaded them to that folder.

**After running the scans, general tasks**

- [ ] Cloud Operations has reviewed the Nessus findings and ensured all daemons are managed by BOSH (see CG04 for context).
- [ ] For any items that require a monthly checkin with a vendor, Cloud Operations has made the appropriate support request to the vendor.

**After running the scans, we've updated the POAM at https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=1701775784 using the following steps**

- [ ] We filed or updated "compliance check" items as POA&M items, based on the ID number and information from the .nessus Nessus compliance reports/exports (`pluginID="x"` is the ID number; `severity="3"` indicates a moderate finding, for example). These don't show up as vulnerabilities in the HTML or web-based Nessus reports, but they need to be tracked as such. We group them together.
- [ ] We updated all columns to include the most recent info about remediations, milestones, statuses, etc., including updating the status date column.
- [ ] We corrected any items that our process indicated were incorrect last time.
- [ ] We moved any web scanner items that should be moved to closed (items originally found by a scanner where we have new scans that prove these things are fixed).
- [ ] We moved any OS and database scanner items that should be moved to closed (items originally found by a scanner where we have new scans that prove these things are fixed).
- [ ] All Nessus items have their Weakness Source Identifier (plug-in ID) filled out in Column F.
- [ ] We listed any new identified web vulnerabilities. (Discard the ones listed as false positives in the SAR, table E-2.)
- [ ] We listed any new identified OS and database vulnerabilities.
- [ ] We did a final check to make sure all columns include recent and accurate info.

**After delivering ConMon report, move this to Awaiting Acceptance and do the following**

- [ ] We updated our Highbar and Atlas boards with current info about POAM items and any necessary followup stories about compliance work and related technical work to prepare for the next month's report.
- [ ] We opened a PR to update our [ConMon checklist template](https://github.com/18F/cg-product/blob/master/ConMonChecklist.md) with any changes from this month.
- [ ] We filed a ConMon report issue for next month, using the checklist template.
