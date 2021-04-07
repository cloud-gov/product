---
name: Deliver ConMon Scans
title: 'Deliver [month] [year] ConMon results by [due date]'
about: INTERNAL ONLY deliver conmon results
labels: compliance
assignees: ''

---


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

# Rough notes on Peter's hacky tracking

* *Set up Google FileStream* - Use from GSA SelfService, the upstream version doesn't seem to work for GSA.
* Have `cg-scripts` in your `$PATH`
* PIP install `nessus-file-reader`
  

I keep everything in `~/Documents/ConMon`, so

```
cd ~/Documents
git clone file:///Volumes/GoogleDrive/My Drive/cloud.gov/Security and Compliance/Compliance/conmon_project.git ConMon
cd ConMon
source conmon.sh
```

That sets up a bunch of shell functions that we run, then copy/paste if they look correct.

* `setup_dir MM DD` - Set up the correct names and places for our copies of the scan
* Drag over from `/Volumes/GoogleDrive/My Drive/18F_ISSO/FedRAMP JAB - cloud.gov - 3PAO Access/ZAP and Nessus results` the 
  * ZAP both XML and HTML
  * RDS *.nessus into the RDS folders
  * Compliance and Vuln *.nessus scans into folders. End result
```
    tree 2021/03
2021/03
├── 20210323-ZAP.html
├── 20210323-ZAP.xml
├── Production-and-Tooling-Vulnerability-and-Compliance-scans_2021-03-23
│   ├── Production_Compliance_scan_wkl5wr.nessus
│   ├── Production_Vulnerability_scan_241iec.nessus
│   ├── Tooling_Compliance_scan_odrbso.nessus
│   └── Tooling_Vulnerability_scan_aogr63.nessus
└── RDS_Compliance_Scans_2021-03-23
    ├── RDS_Compliance_-_Credhub_Prod_xctauy.nessus
    ├── RDS_Compliance_-_Credhub_Tooling_hi0ovb.nessus
    ├── RDS_Compliance_-_OpsUAA_Tooling_lnptdj.nessus
    ├── RDS_Compliance_Scan_-_ATC_Tooling_fmtjza.nessus
    ├── RDS_Compliance_Scan_-_Bosh_Tooling_6maygg.nessus
    ├── RDS_Compliance_Scan_BOSH_Prod_9nbxn6.nessus
    └── RDS_Compliance_Scan_CF_Prod_k9ysxd.nessus
```
* Run `prep_nessus` function
  * This generates `MM.nessus_summary` and `MM.nessus_work` - This month's summary is compared, using `comm` to last month's summary. 
* Review `MM.nessus_summary`, and Git add/commit it if it's OK.
* The file `MM.nessus_work` looks like this:
```
LAST MONTH (fixed)
	THIS MONTH (new)
		BOTH  (persisting)
	147163, Risk: Medium, Plugin Name: Apache Tomcat 7.0.0 < 7.0.108 RCE, https://www.tenable.com/plugins/nessus/147163
   ..hostnames or number of impacted hosts
```
The items left-aligned are ones that we're in last months' report but are now fixed, the next indent are those that are new (present now, absent last month), and the third indent are present in both months' scans (persisting issues)
* Move the fixed items to Done in the POAM spreadsheet, updating the status date
* Add the new items
  * run `parse-nessus-xml.py` and get the CVS output.
  * paste into POAM spreadsheet, then used the `Data` menu to convert to `Split Text to Columns`
  * fix up the entry
  * copy down the formula for Column M, "Scheduled Completion Date", to generate the due date based on severity
* Use the `prep_zap` function for ZAP scan consolidation
* Move fixed issues from Open to Closed tabs. Be sure to
  * Update the Status Date
  * Update the Supporting Documents, unless routine stemcell patch covered by the scan output

Be sure to
* Review the RDS scans
* Review the Compliance scans
* Review the Inventory

For the RDS inventory (This need improving)
* See the file `parse_rds.sh`

**Acceptance criteria**
- [ ] We uploaded our POA+M summary to MAX.gov https://community.max.gov/display/FedRAMPExternal/18F+Continuous+Monitoring 'POA&M and Inventory' folder
- [ ] We uploaded our Inventory sheet to MAX.gov  https://community.max.gov/display/FedRAMPExternal/18F+Continuous+Monitoring 'POA&M and Inventory' folder
- [ ] We uploaded our Nessus and OWASP scan results to MAX.gov to https://community.max.gov/display/FedRAMPExternal/18F+Vulnerability+Scans
- [ ] We uploaded the Summary Excel sheet to https://community.max.gov/display/FedRAMPExternal/18F+Continuous+Monitoring
- [ ] We created next month's issue for this task and for running the scans.