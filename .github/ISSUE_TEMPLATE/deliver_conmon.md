## Deliver [month] [year] ConMon scans by [due date]

In order for us to update the JAB on our compliance in a consistent way, we need to deliver a Continuous Monitoring report on [due date]. (our standard due date is the 2nd of the month. If these dates fall on a weekend or federal holiday, adjust to the last business day before the date.)

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary). 


We need to process our scan results and prepare documentation for any updated or new items, including updating the [POAM](https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=1701775784).

We always have to do these tasks:

* List any new identified vulnerabilities.
   * Check for sneaky Nessus findings that apply to only a subset of components. Use the [Nessus parse script](https://github.com/18F/cg-scripts/blob/master/parse-nessus-xml.py) to help.
   * Discard the ones listed as false positives in the POAM open and closed tabs.
   * The [OWASP ZAP parse script](https://github.com/18F/cg-scripts/blob/master/parse-owasp-zap-xml.py) can help.
* Move any scanner items that should be moved to closed (items originally found by a scanner where we have new scans that prove these things are fixed).
* Update all columns to include the most recent info about remediations, milestones, statuses, etc., including updating the status date column.
* Cloud Operations needs to review the Nessus findings and ensure all daemons are managed by BOSH (see CG04 for context).
* Update cell D3 if you don't want `=today()` to be the date for this POA&M. 
* Copy the [the summary cover sheet template](https://drive.google.com/drive/folders/1oUmCq_YHJoE3EeR6a-pfE3i4D1ZzFUiL) and fill it out.

Depending on scan results, we sometimes also have to do these tasks:

* For any items that require a monthly checkin with a vendor, Cloud Operations needs to make the appropriate support request to the vendor.
* Write Deviation Requests for operational requirements, risk adjustments, and false positives.
* Update our boards with current info about POAM items and any necessary followup stories about compliance work and related technical work to prepare for the next month's report.
* Open a PR to update our [ConMon checklist template](https://github.com/18F/cg-product/blob/master/ConMonChecklist.md).

**Acceptance criteria**
- [ ] We uploaded our POA+M summary to MAX.gov https://community.max.gov/display/FedRAMPExternal/18F+Continuous+Monitoring 'POA&M and Inventory' folder
- [ ] We uploaded our Inventory sheet to MAX.gov  https://community.max.gov/display/FedRAMPExternal/18F+Continuous+Monitoring 'POA&M and Inventory' folder
- [ ] We uploaded our Nessus and OWASP scan results to MAX.gov to https://community.max.gov/display/FedRAMPExternal/18F+Vulnerability+Scans
- [ ] We uploaded the Summary Excel sheet to https://community.max.gov/display/FedRAMPExternal/18F+Continuous+Monitoring
- [ ] We created next month's issue for this task and for running the scans.