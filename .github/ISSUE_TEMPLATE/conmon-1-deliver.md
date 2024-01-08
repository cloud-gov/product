---
name: ConMon - Deliver Scans
title: 'Deliver [month] [year] ConMon results by [due date]'
about: INTERNAL ONLY deliver conmon results
labels: compliance
assignees: ''

---
In order for us to update the JAB on our compliance in a consistent way, we need to deliver a Continuous Monitoring report monthly (our standard due date is the 2nd of the month. If these dates fall on a weekend or federal holiday, adjust to the last business day before the date.)

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary). 

We need to process our scan results and prepare documentation for any updated or new items, including updating the [vulnerability tracker](https://docs.google.com/spreadsheets/d/1tAYNmiEUwMSquRcQ0MrqtP-VIo7oxh1OzD6rmkWl-9w/edit#gid=1701775784) and [POA&M](https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=1701775784).
(Vulnerabilities that are patched within RA-05/SI-02 deadlines are not reported on the POA&M sheet).



## Workstation Processing

### First time setup

* *Set up Google Drive* -  install from GSA SelfService
* Have `cg-scripts` in your `$PATH`
* PIP install `nessus-file-reader`
  
I keep all the conmon materials locally in `~/Documents/ConMon`, and have a symlink 
to the few scripts that I use for parsing the conmon materials, as follows:

* Clone [cg-compliance](git@github.com:cloud-gov/cg-compliance.git) to the location of your choice
* Make a symlink from ~/Documents/Conmon to the scripts' bin directory: 
     ```
     cd ~/Documents/ConMon
     # Note - pending merge of PR https://github.com/cloud-gov/cg-compliance/pull/264
     ln -s (cg-compliance-path)/conmon/bin .
    ```

## Monthly processing


* `cd ConMon; source bin/conmon.sh` - Set up functions for conmon
* `setup_dirs YYYY MM DD` - Set up the correct names, env vars, and places for our copies of the scan
* Open in separate finder windows
   * the new target folder (e.g. `ConMon/2021/11`) 
   * the Google Drive with  `ZAP and Nessus results/2021-11-22`
* Drag scans from Drive to their local targets
  * ZAP: copy both XML and HTML to the top level
  * RDS *.nessus into the RDS folders
  * Compliance and Vuln *.nessus scans into "Production-and-Tooling..." folders. End result:
  ```
   tree $MonthDir
    /Users/peterdburkholder/Documents/ConMon/2023/11
    ├── 20231122-ZAP-external.html
    ├── 20231122-ZAP-external.xml
    ├── 20231122-ZAP-internal.html
    ├── 20231122-ZAP-internal.xml
    ├── 20231128-ZAP-pages.html
    ├── 20231128-ZAP-pages.xml
    ├── Production-and-Tooling-Vulnerability-and-Compliance-scans_2023-11-22
    │   ├── Production Compliance scan_6zil6h.nessus
    │   ├── Production Vulnerability scan_awsge2.nessus
    │   ├── Tooling Compliance scan_e16nva.nessus
    │   └── Tooling Vulnerability scan_amokaf.nessus
    └── RDS_Compliance_Scans_2023-11-22
        ├── RDS Compliance - Credhub Prod_v4ek1g.nessus
        ├── RDS Compliance - Credhub Tooling_vwal0v.nessus
        ├── RDS Compliance - OpsUAA Tooling_hc5sqs.nessus
        ├── RDS Compliance Scan - ATC Tooling_l6a0hm.nessus
        ├── RDS Compliance Scan - Bosh Tooling_enkk7f.nessus
        ├── RDS Compliance Scan BOSH Prod_9r1y4q.nessus
        └── RDS Compliance Scan CF Prod_ipvc66.nessus
  ```
* Replace spaces in filenames with underscores:
  ```shell
  pushd Production-and-Tooling-Vulnerability-and-Compliance-scans_2021-03-23
  spaces2underscores
  cd ../RDS_Compliance_Scans_2021-03-23
  spaces2underscores
  popd
  ```
* Run `nessus_log4j`. This generates a table something like this: 
  ```
  ------- Log4J REPORT  ------
  Log4j plugin:  155999
	Log4J violations on Diego cells on phantom paths (safe):  0
	Log4J violations on Diego cells in customer path (safe):  6
	Log4J violations on Logstash nodes at known path (safe):  27
	Log4J violations of unknown origins found (UNSAFE)     :  0
  ```
  * If there are any UNSAFE findings:
    * Create a new issue in https://github.com/cloud-gov/private
    * Link to the issue in a comment, below
    * Immediately assign to CloudOps and discuss with them
  * Once clean, screenshot and attach to this issue.
* Run `nessus_daemons`
  * Review any findings, if they're legitimate daemon, open an issue in [cg-scripts](https://github.com/cloud-gov/cg-scripts) to patch `parse-nessus-xml.py`.
  * Link to the issue, or PR, in the comments below
  * If they're suspicious, follow our IR processes.
  * Once clean, screenshot and attach to this  issue.
* Run `prep_nessus` function
  * This generates `MM.nessus_summary.txt` and `MM.nessus_work.txt` - This month's summary is compared, using `comm` to last month's summary. 
* Review `MM.nessus_summary.txt`, see if it's OK.
* The file `MM.nessus_work.txt` looks like this:
```
LAST MONTH (fixed)
	THIS MONTH (new)
		BOTH  (persisting)
	147163, Risk: Medium, Plugin Name: Apache Tomcat 7.0.0 < 7.0.108 RCE, https://www.tenable.com/plugins/nessus/147163
   ..hostnames or number of impacted hosts
```
The items left-aligned are ones that we're in last months' report but are now fixed, the next indent are those that are new (present now, absent last month), and the third indent are present in both months' scans (persisting issues)
* Run `nessus_csv` to generate the `MM.nessus.csv` file for the Vuln Tracker Spreadsheet
* Run `prep_zap` to generate the summary OWASP ZAP files.
* Copy the new `.txt` and the CSV files to [Google Drive](https://drive.google.com/drive/folders/1A4jVPmlnO2KHiSFVFxfp4Gp2nl5CFGPD) for the Summary File Processing (below)

* Review the RDS scans:
  - cd to the directory with the RDS compliance scans,
  - run `../../../bin/parse-rds.sh`
  - if there are version out-of-date findings, see latest version in AWS with:
    - `aws rds describe-db-engine-versions --output=table --engine postgres --engine-version X.Y`
* Review the Compliance scans: 
  * No good parsing yet, review manually

Before the summary file processing, confirm that you have 

- [ ] Reviewed the `parse-nessus` log4j findings 
- [ ] Reviewed the `parse-nessus` daemon results
- [ ] Sanity checked the
  - MM.nessus_summary.txt
  - MM.nessus_work.txt
  - MM.zap_summary.txt
  - MM.zap_work.txt
  - MM.nessus.csv
- [ ] Reviewed the Compliance scans on the Nessus manager for new findings

## Summary file processing

These steps can be done the same person who did the work above, or passed on
to a compliance specialist.

### Process the Nessus and Zap `_work.txt` and CSV file

* Review the findings and compare them to the Google Sheets vulnerability tracker
* Move the fixed items to Done in the vulnerability tracker, updating the status date
* Add the new items
  * Open the `MM.nessus.csv` in Excel and copy all the new findings
  * Paste the new findings put into the vulnerability tracker
  * fix up the entry
  * copy down the formula for Column M, "Scheduled Completion Date", to generate the due date based on severity

### Manage the POA&Ms, Inventory, and ConMon Summary

* Any Java and Tomcat findings will require work outside our normal stemcell patching. See [closed issues in the private repository](https://github.com/cloud-gov/private/issues?q=is%3Aissue+is%3Aopen+in%3Atitle+OpenJDK+OR+Java+OR+Tomcat) for examples
* Work through the `MM.zap_work.txt` file produced by `prep_zap`, above
* Pay special attention to the High and Moderate findings
* Move fixed issues from Open to Closed tabs. Be sure to
  * Update the Status Date
  * Update the Supporting Documents, unless routine stemcell patch covered by the scan output

* Review the Inventory
  * Update RDS postgres versions if necessary

* Address all gravely late POA&Ms
  * Go to the [POA&M Dashboard](https://docs.google.com/spreadsheets/d/1Of4psOutBmZHVekV-_n_CuG8lOqbdpmrSQQJeSwobm0/edit#gid=232277195)
  * For each 90+day late POA&M, be sure to update the Milestone Changes filed
    of the POA&M sheet
* Manage the container scans:
  * Create a scan folder: "container-scans-YYYY-MM-DD/" 
  * Go to https://groups.google.com/a/gsa.gov/g/cloud-gov-compliance and get the emailed container scan attachments.
  * Download the scans from the 22nd of the month to the scan folder
  * Review the Scan results with TKTK

### Be sure you've done all the following

* List any new identified vulnerabilities in the vulnerability tracker.
* Move any scanner items that should be moved to closed (items originally found by a scanner where we have new scans that prove these things are fixed).
* Update all columns to include the most recent info about remediations, milestones, statuses, etc., including updating the status date column.
* Cloud Operations needs to review the Nessus findings and ensure all daemons are managed by BOSH (see CG04 for context).
* Add any late vulnerabilities to the POA&M worksheet (i.e. vulnerabilities that will be remediated later than 30, 90 or 180 days old).
* Update cell D3 to be the current date for this POA&M (date of submission). 
* Copy the [the summary cover sheet template](https://drive.google.com/drive/folders/1oUmCq_YHJoE3EeR6a-pfE3i4D1ZzFUiL) and fill it out.

Depending on scan results, we sometimes also have to do these tasks:

* For any items that require a monthly checkin with a vendor, Cloud Operations needs to make the appropriate support request to the vendor.
* Write Deviation Requests for operational requirements, risk adjustments, and false positives.
* Update our boards with current info about vulnerabilities and open POAM items and any necessary followup stories about compliance work and related technical work to prepare for the next month's report.
* Open a PR to update our [ConMon checklist template](https://github.com/18F/cg-product/blob/master/ConMonChecklist.md).

## Upload to the FedRAMP repository

* (Needs updating once the new repository is ready)

## Acceptance criteria

- [ ] We have created/resolved any issues with Nessus Log4J findings
- [ ] We have created/resolved any issues with Nessus unknown daemon findings
- [ ] We have added the Container scan results 
- [ ] We uploaded our POA+M summary to MAX.gov https://community.connect.gov/display/FedRAMPExternal/18F+Continuous+Monitoring 'POA&M and Inventory' folder
- [ ] We uploaded our Inventory sheet to MAX.gov  https://community.connect.gov/display/FedRAMPExternal/18F+Continuous+Monitoring 'POA&M and Inventory' folder
- [ ] We uploaded our Nessus and OWASP scan results to MAX.gov to https://community.connect.gov/display/FedRAMPExternal/18F+Vulnerability+Scans
- [ ] We uploaded our container scans ....
- [ ] We uploaded the Summary Excel sheet to https://community.connect.gov/display/FedRAMPExternal/18F+Continuous+Monitoring
- [ ] We updated, if necessary, the issue template for next month

There! You've completed KHAN!-mon 

![Kirk's KHAN](https://media.tenor.com/zpkXBVeJPXAAAAAC/star-trek-the-wrath-of-khan-star-trek2.gif)
