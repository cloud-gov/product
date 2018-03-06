# Continuous Monitoring Checklist

## Instructions

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary). After delivery of a monthly ConMon report:

1. Make sure there are new stories in the appropriate places in the cloud.gov task tracker called "Run [month] ConMon scans" and "Deliver [month] ConMon report", with due dates on the issues. Our standard scan date is the 23rd of the month, and our standard due date is the 2nd of the month. If these dates fall on a weekend or federal holiday, adjust to the last business day before the date.
1. Copy everything below the line into the stories, with checklists for the checklist items.
1. Replace [due date] with the next due date.

---

## Run [month] ConMon scans

In order for us to update the JAB on our compliance in a consistent way, we need to run Continuous Monitoring scans on approximately the 23rd of the month.

Check that you have the [latest stable version of ZAP](https://github.com/zaproxy/zaproxy/wiki/Downloads).

- [ ] We ran OWASP ZAP on the following domains using steps #1-6 of the manual scanning instructions at https://before-you-ship.18f.gov/security/dynamic-scanning/#scanning - authenticated, passive and active: https://ci.fr.cloud.gov/, https://dashboard.fr.cloud.gov/, https://account.fr.cloud.gov/, https://cloud.gov/, https://idp.fr.cloud.gov/, https://login.fr.cloud.gov/,  https://opslogin.fr.cloud.gov/login, https://logs.fr.cloud.gov/, https://admin.fr.cloud.gov/, https://prometheus.fr.cloud.gov/ , https://grafana.fr.cloud.gov/, https://alertmanager.fr.cloud.gov/, https://logs-platform.fr.cloud.gov/.
  - Load the [cloud.gov conmon](https://raw.githubusercontent.com/18F/cg-product/master/cloud.gov-conmon.context) ZAP context from this repository.
    - Check the context file to see if it needs updating (update if necessary).
  - You have to log in so that ZAP can scan inside the authenticated websites, which includes being on the VPN.
  - Make sure to scan _only_ those sites, rather than browsing other URLs while ZAP is running, to prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report).
- [ ] We exported and uploaded those fresh OWASP ZAP results in XML format to a folder in the folder at https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U
- [ ] We also grabbed the OWASP ZAP scans in human-readable HTML format and uploaded them to that folder.
- [ ] We grabbed a fresh set of Nessus scans (both OS and database/RDS) from https://nessus.fr.cloud.gov/ in .nessus format and uploaded the fresh results to a folder in the folder at https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U - requires auth (Cloud Ops or Deputy Director).
- [ ] We also grabbed the Nessus HTML export - https://docs.tenable.com/nessus/6_8/Content/Exported_Results.htm - for those scans and uploaded them to that folder.
- [ ] We updated the [POAM Inventory tab](https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=2017890110). From tooling and production BOSH inventory:

  - `bosh vms --vitals | grep -e "^\w" | awk '{print $1","$4","$3}' | sed -e 's/\/[a-z0-9\-]*,/,/' |sed -e 's/,z1/,us-gov-west-1a/' | sed -e 's/,z2/,us-gov-west-1b/'`

## Deliver [month] ConMon scans

In order for us to update the JAB on our compliance in a consistent way, we need to deliver a Continuous Monitoring report on [due date].

We need to process our scan results and prepare documentation for any updated or new items, including updating the [POAM](https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=1701775784).

We always have to do these tasks:

* List any new identified vulnerabilities.
   * Check for sneaky Nessus findings that apply to only a subset of components.
   * Discard the ones listed as false positives in the POAM open and closed tabs.
   * The [OWASP ZAP parse script](https://github.com/18F/cg-scripts/blob/master/parse-owasp-zap-xml.py) can help.
* Move any scanner items that should be moved to closed (items originally found by a scanner where we have new scans that prove these things are fixed).
* Update all columns to include the most recent info about remediations, milestones, statuses, etc., including updating the status date column.
* Cloud Operations needs to review the Nessus findings and ensure all daemons are managed by BOSH (see CG04 for context).

Depending on scan results, we sometimes also have to do these tasks:

* For any items that require a monthly checkin with a vendor, Cloud Operations needs to make the appropriate support request to the vendor.
* File any new failed "compliance check" items as POA&M items, based on the ID number and information from the .nessus Nessus compliance reports/exports (`pluginID="x"` is the ID number; `severity="3"` indicates a moderate finding, for example). These don't show up as vulnerabilities in the HTML or web-based Nessus reports, but they need to be tracked as such.
* Update our boards with current info about POAM items and any necessary followup stories about compliance work and related technical work to prepare for the next month's report.
* Open a PR to update our [ConMon checklist template](https://github.com/18F/cg-product/blob/master/ConMonChecklist.md).

**Acceptance criteria**
-  [ ] We uploaded our files to MAX.gov and emailed relevant FedRAMP team members to let them know that's done
