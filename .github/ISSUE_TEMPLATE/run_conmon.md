---
name: Run ConMon Scans
title: 'Run [month] [year] ConMon scans'
about: INTERNAL ONLY schedule conmon runs
labels: compliance
assignees: ''

---

In order for us to update the JAB on our compliance in a consistent way, we need to run Continuous Monitoring scans on approximately the 23rd of the month. (If this date falls on a weekend or federal holiday, adjust to the last business day before the date.)

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary).

## Netsparker

Omit: I am not finding a clear path to using Netsparker for our admin apps, and NetSparker has its own issues with false positives



# OWASP ZAP Scans

## Preliminary work

We scan our externally facing apps as sandbox users of cloud.gov. This vastly speeds up scans since the spider doesn't crawl every app and org in _logs_ or _dashboard_, and also avoids issues with the "clcking" on links with undesired impacts. Create a sanbox account, starting from https://account.fr.cloud.gov/signup, and use an email such as your `fname.lname@{cio.gov, pif.gov, fedramp.gov}`

As your "sandbox" user identity, launch a "Hello World" app so there's something in the dashboard and logs apps to spider. (ToDo: Determine if this is really necessary)

## Install, Configure, and Update

- Check that you have the [latest stable version of ZAP](https://www.zaproxy.org/download/) or install via Homebrew with `brew cask install (or brew upgrade --cask) owasp-zap` (recommended). Upgrade if necessary.

     > NOTE: If you see an error running ZAP as an unsigned application, run the following from the command line: `xattr -dr com.apple.quarantine '/Applications/OWASP ZAP.app'`

- Start ZAP and update
  - For "Session persistence", select "No, I do not want to persist my session..."
  - For "Manage add-ons", select "Update All" 
  - ZAP ->  Preferences -> Options:
    - JVM -> JVM options:  `-Xmx8192m`
    - Active Scan:  
      - 3 hosts
      - 5 threads
    - Global Exclude URL:
      - Site - Firefox (select all)
      - Site - Font CDNs
      - Site - Mozilla CSN
      - Spider
        - Max Depth to Crawl: 5
        - Number of Threads: 7

### Quit and restart ZAP if you change the JVM options

- Be sure you have Firefox installed (with Homebrew `brew cask install firefox` or any way you chose). Chrome does not support proxy settings while Firefox does.

- `git clone git@github.com:cloud-gov/product.git` so you have the `context` files you need.

## Running ZAP scans

ZAP scans take hours. We recommend you start in the morning. There are two separate scans to run and the second one takes considerably longer than the first.

- From the cloud.gov `product` repo, load the cloud.gov `cloud.gov-conmon-external.context` into ZAP (File > Import Context)
  - Delete the "Default Context" or any already completed context.
- On the top line of icons, there should be a Firefox icon on the far right. Double-click that to open Firefox preconfigured to proxy through ZAP.
- Open the `context` to see the included web applictions (Context -> Included in Context)
- In the ZAP-configured Firefox, log in to each site in the context list.
  - For the `external` context, use your "sandbox" identity. VPN not needed.
  - For the `internal` context, use your Cloud Ops (GSA SecureAuth) identity, and join the VPN
- To prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report), review the `Sites` list to ensure only the cloud.gov sites have a small red circle/sight on them (denoting the site will be included). Remove any sites not needed by CTRL-clicking on them and selecting `Delete`.
- CTRL-click on the context and run the `Spider` scan.  This takes a little less than an hour.
- After the `Spider` scan is complete, again CTRL-click on the context and this time run the `Active Scan`. 
- After both scans are complete, export the results as both XML and HTML from the `Reports` menu. Name the files according to `YYYYMMDD-ZAP-(context).xml/html`. E.g.
  - 20210623-ZAP-internal.xml
  - 20210623-ZAP-internal.html
  - 20210623-ZAP-external.xml
  - 20210623-ZAP-external.html

Repeat the above steps for the `internal` context (which will require the VPN) 

- Upload all reports to Google Drive: https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U in a folder named `YYYYMMDD-ZAP-Nessus`.

You can shut down ZAP and Firefox. 

NEEDS FIXING: Include for 2021-07 the Pages scanning:
  * PAGES: For scanning cloud.gov Pages (while in pre-release status), download the [pages_staging_conmon.context]().
  * PAGES: Or the Pages context, for scanning those apps.

## Potential ZAP Issues

### Disk Usage

A single ZAP scan of the cloud-gov context requires significant disk space (over 100GB). If you have run ZAP previously, you should check to see if you previous sessions have been persisted. If so, you likely need to clear out those directories before proceeding.

You can check ZAP's disk usage with:

```
du -h -d 1 ~/Library/Application\ Support/ZAP/
```

If you see an abnormally large `session` or `sessions` directory (my last run was 132G), you likely want to delete all files in these directories before proceeding.  Choosing to "Not persist" sessions should alleviate this issue.

## Export Nessus Scans

- Log in to Nessus: https://nessus.fr.cloud.gov/

- Select `All Scans`

- Click on each scan except for staging, and export the .nessus file (Export > Nessus) and the Executive Summary report (Report > HTML).

- [ ] Upload all exports (both Executive Summary and .nessus files) to the same Google Drive folder you put the ZAP scans in.

## Update the POAM Inventory sheet

A python script is used to generate the inventory list.

- Open the [POAM Inventory sheet](https://docs.google.com/spreadsheets/d/1_9Neq8fGO4NdQhsqLXDn445g3GUa1k_FZUrUXc7hulY/edit#gid=1371600163)

- Delete the data rows (**starting after the RDS database listings**) - These rows are locked to prevent inadvertent editing.

- For the tooling and production jumpboxes, login to each of them and from the initial home directory you start in, run `python3 cg-scripts/generate-POAM-inventory.py`. This will output data to your terminal window in CSV format. Copy the entire CSV output.

- Paste the contents in the spreadsheet by selecting the first cell in row 3 then pasting with CTRL-Shift-V to paste without formatting. Then select the paste icon that appears and click `Split text to columns`

- [ ] Verify you have pasted the inventory for both production and tooling.
