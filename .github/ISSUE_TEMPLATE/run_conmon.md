---
name: Run ConMon Scans
title: 'Run [month] [year] ConMon scans'
about: INTERNAL ONLY schedule conmon runs
labels: compliance
assignees: ''

---

In order for us to update the JAB on our compliance in a consistent way, we need to run Continuous Monitoring scans on approximately the 23rd of the month. (If this date falls on a weekend or federal holiday, adjust to the last business day before the date.)

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary). 

## Running ZAP Scans

ZAP scans take hours. We recommend you start in the morning. There are two separate scans to run and the second one takes considerably longer than the first.

- Check that you have the [latest stable version of ZAP](https://www.zaproxy.org/download/) or install via Homebrew with `brew cask install (or brew upgrade --cask) owasp-zap` (recommended). Upgrade if necessary.

     > NOTE: If you see an error running ZAP as an unsigned application, run the following from the command line: `xattr -dr com.apple.quarantine '/Applications/OWASP ZAP.app'`

- Be sure you have Firefox installed (with Homebrew `brew cask install firefox` or any way you chose). Chrome does not support proxy settings while Firefox does.

- Configure ZAP as a proxy for Firefox: https://www.zaproxy.org/docs/desktop/start/proxies/

- Download the [cloud.gov conmon](https://raw.githubusercontent.com/18F/cg-product/master/cloud.gov-conmon.context) cloud.gov context from this repository and update it if necessary

- Load the cloud.gov context into ZAP (File > Import Context)
     
- You have to log in to each site in the context list so that ZAP can scan inside the authenticated websites. You have to be on the VPN. In Firefox, log in to each site in the context list. You can see the list by clicking the `cloud.gov common` context > Include in Context.

- To prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report), review the `Sites` list to ensure only the cloud.gov sites have a small red circle/sight on them (denoting the site will be included). Remove any sites not needed by CTRL-clicking on them and selecting `Delete`.

- CTRL-click on the `cloud.gov common` context and run the `Spider` scan.  This takes a little less than an hour.

- After the `Spider` scan is complete, again CTRL-click on the `cloud.gov common` context and this time run the `Active Scan`. This takes at least 4-5 hours, minimum.

- After both scans are complete, export the results as both XML and HTML from the `Reports` menu. Name the files according to `YYYYMMDD-ZAP.xml/html`.

- [ ] Upload both reports to Google Drive: https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U in a folder named `YYYYMMDD-ZAP-Nessus`.

You can shut down ZAP and Firefox. If you use Firefox in your day to day, you likely want to remove the proxy.

## Export Nessus Scans

- Log in to Nessus: https://nessus.fr.cloud.gov/

- Select `All Scans`

- Click on each scan except for staging, and export the .nessus file (Export > Nessus) and the Executive Summary report (Report > HTML).

- [ ] Upload all exports (both Executive Summary and .nessus files) to the same Google Drive folder you put the ZAP scans in.

## Update the POAM Inventory sheet

A python script is used to generate the inventory list.

- Open the [POAM Inventory sheet](https://docs.google.com/spreadsheets/d/1_9Neq8fGO4NdQhsqLXDn445g3GUa1k_FZUrUXc7hulY/edit#gid=1371600163)

- Delete the data rows (starting after the RDS database listings)

- For the tooling and production jumpboxes, login to each of them and from the initial home directory you start in, run `python3 cg-scripts/generate-POAM-inventory.py`. This will output data to your terminal window in CSV format. Copy the entire CSV output.

- Paste the contents in the spreadsheet by selecting the first cell in row 3 then pasting with CTRL-Shift-V to paste without formatting. Then select the paste icon that appears and click `Split text to columns`

- [ ] Verify you have pasted the inventory for both production and tooling.
