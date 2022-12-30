---
name: Run ConMon Scans
title: "Run [month] [year] ConMon scans"
about: INTERNAL ONLY schedule conmon runs
labels: compliance
assignees: ""
---

In order for us to update the JAB on our compliance in a consistent way, we need to run Continuous Monitoring scans on approximately the 23rd of the month. (If this date falls on a weekend or federal holiday, adjust to the last business day before the date.)

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary).

## Netsparker

Omit: I am not finding a clear path to using Netsparker for our admin apps, and NetSparker has its own issues with false positives

# OWASP ZAP Scans

From the [ZAP documentation](https://www.zaproxy.org/getting-started/): "Zed Attack Proxy (ZAP) is a free, open-source penetration testing tool being maintained under the umbrella of the Open Web Application Security Project (OWASP). ZAP is designed specifically for testing web applications and is both flexible and extensible."

We run ZAP from a platform operator's local machine. ZAP opens a Firefox instance that is configured to proxy all requests through ZAP. ZAP can then analyze and modify the requests.

## Preliminary work - Sandbox User Setup

We scan our externally facing apps as _sandbox users_ of cloud.gov, via the cloud.gov IdP, instead of _platform admins_. This vastly speeds up scans since the spider doesn't crawl every app and org in _logs_ or _dashboard_, and also avoids issues with ZAP "clicking" on links with undesired impacts.

Create a sandbox account, starting from https://account.fr.cloud.gov/signup, and use an email such as your `fname.lname@{cio.gov, pif.gov, fedramp.gov}`

As your "sandbox" user identity, launch a "Hello World" app so there's something in the dashboard and logs apps to spider. (ToDo: Determine if this is really necessary, provide link to steps).

## Install, Configure, and Update

- Check that you have the [latest stable version of ZAP](https://www.zaproxy.org/download/). Install/update via Homebrew with:
  - `brew update; brew install owasp-zap` or
  - `brew update; brew reinstall owasp-zap`
  > NOTE: If you see an error running ZAP as an unsigned application, run the following from the command line:
  - `xattr -dr com.apple.quarantine '/Applications/OWASP ZAP.app'`
  - ZAP also has a [weekly build](https://www.zaproxy.org/download/#weekly) available. If the current stable build isn't working for some reason, try the weekly build instead. Download the ZIP, `cd` to it in your terminal, and run it with `./zap.sh`. If it outputs a message like `Exiting: ZAP requires a minimum of Java 11 to run`, run `brew install java` to install the latest Java and try again.
- Start ZAP and update
  - For "Session persistence", select "No, I do not want to persist my session..."
  - For "Manage add-ons", select "Update All"
  - ZAP -> Preferences -> Options:
    - JVM -> JVM options: `-Xmx8192m`
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

ZAP scans take hours. We recommend you start in the morning. There are two separate scans to run, external and internal, and the internal one takes considerably longer (you may want to run it when VPN traffic is lower)

The following steps are for the `external` scan (except as noted):

- From the cloud.gov `product` repo, load the cloud.gov `cloud.gov-conmon-external.context` into ZAP (File > Import Context)
  - Delete the "Default Context" or any already completed context.
- On the top line of icons, there should be a Firefox icon on the far right. Click that to open Firefox preconfigured to proxy through ZAP.
- Open the `context` to see the included web applications (Context -> Included in Context)
- In the ZAP-configured Firefox, log in to each site in the context list.
  - For the **`external` context, use your "sandbox" identity**. VPN not needed.
  - For the **`internal` context, use your Cloud Ops (GSA SecureAuth) identity**, and join the VPN
- To prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report), review the `Sites` list to ensure only the cloud.gov sites have a small red circle/sight on them (denoting the site will be included). Remove any sites not needed by CTRL-clicking on them and selecting `Delete`.
  - On the `internal` rescan, you can omit `login.fr.cloud.gov` from the sites before spidering/scanning
- CTRL-click on the context and run the `Spider` scan. This takes a little less than an hour.
- After the `Spider` scan is complete, again CTRL-click on the context and this time run the `Active Scan`.
- After the Spider and Active scans are complete, export the results:
  - From `Report` menu, select `Generate Report ...`
    - Select the `Template` options, and use the templates:
      - Traditional HTML report
      - Traditional XML report
    - Name the files according to `YYYYMMDD-ZAP-(context).xml/html`. E.g.
      - 20210623-ZAP-external.xml
      - 20210623-ZAP-external.html
    - Optional: Check with compliance lead on whether we also need
      "Traditional HTML Report with Requests and Responses"

**Quit ZAP, then repeat the "Running ZAP scans" steps for the `internal` context (which will require the VPN)**

## Troubleshooting ZAP Scans

In Firefox if you see a Java Unable to Connect Exception, try the following:

Close both Firefox and ZAP.

In `~/Library/Application Support/ZAP/log4j2.properties`:

Change the following level's to debug so the entries look like this:

```
logger.paros.name = org.parosproxy.paros
logger.paros.level = debug

logger.zap.name = org.zaproxy.zap
logger.zap.level = debug
```

Open ZAP, follow the above and open Firefox. Try to go to the server that failed previously.

If that works, then change the levels back to info from debug, so they look like this:

```
logger.paros.name = org.parosproxy.paros
logger.paros.level = info

logger.zap.name = org.zaproxy.zap
logger.zap.level = info
```

For the internal sites, try the following order in Firefox to bring up the sites according to the context:

```
https://ci.fr.cloud.gov
https://admin.fr.cloud.gov
https://alertmanager.fr.cloud.gov
https://logs-platform.fr.cloud.gov
https://grafana.fr.cloud.gov
https://prometheus.fr.cloud.gov
https://opslogin.fr.cloud.gov
```

If the context changes the sites, this list and order will need to be revisited.

Stop any locally running web servers as their port forwarding can prevent the Firefox proxying from working correctly (you might see the error: "browser was not found")

## Upload and wrap up

Upload all reports to Google Drive: https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U in a folder named `YYYYMMDD-ZAP-Nessus`.

You can shut down ZAP and Firefox.

## Potential ZAP Issues

## Acceptance criteria

- [ ] YYYYMMDD-external.xml ZAP scan is present in YYYYMMDD-ZAP-Nessus folder
- [ ] YYYYMMDD-internal.xml ZAP scan is present in YYYYMMDD-ZAP-Nessus folder
- [ ] YYYYMMDD-pages.xml ZAP scan is present in YYYYMMDD-ZAP-Nessus folder

### Disk Usage

A single ZAP scan of the cloud-gov context requires significant disk space (over 100GB). If you have run ZAP previously, you should check to see if you previous sessions have been persisted. If so, you likely need to clear out those directories before proceeding.

You can check ZAP's disk usage with:

```

du -h -d 1 ~/Library/Application\ Support/ZAP/

```

If you see an abnormally large `session` or `sessions` directory (my last run was 132G), you likely want to delete all files in these directories before proceeding. Choosing to "Not persist" sessions should alleviate this issue.

## Export Nessus Scans

- Log in to Nessus: https://nessus.fr.cloud.gov/
- Select `All Scans`
- Click on each vulnerability scan for Tooling and Production, and export the .nessus file (Export > Nessus) and the "Complete List of Vulnerabilities by Host" report (Report > HTML).
- Click on each compliance  scan for Tooling and Production, and export the .nessus file (Export > Nessus) and the "Compliance" report (Report > HTML).
- Click on each scan for RDS Compliance, and export the .nessus file (Export > Nessus) and the "Compliance" report (Report > HTML).

## Acceptance criteria:

The following (.nessus and .html) are all uploaded to YYYYMMDD-ZAP-Nessus folder:

- [ ] Production_Vulnerability_scan
- [ ] Tooling_Vulnerability_scan
- [ ] Production_Compliance_scan
- [ ] Tooling_Compliance_scan
- [ ] ALL the RDS compliance scans

## Update the POAM Inventory sheet

A python script is used to generate the inventory list.

- Open the [POAM Inventory sheet](https://docs.google.com/spreadsheets/d/1_9Neq8fGO4NdQhsqLXDn445g3GUa1k_FZUrUXc7hulY/edit#gid=1371600163)

- Delete the data rows (**starting after the manually maintained inventory items**) - These rows are locked to prevent inadvertent editing.

- For the tooling and production jumpboxes:
  - Login to each jumpbox and take note of the container number.
  - Run `python3 cg-scripts/generate-POAM-inventory.py > inv.csv`, then `exit`.
  - Copy the CSV to your local clipboard by running `fly -t ci i -j "jumpbox/container-bosh-{environment}" -s jumpbox -b "{container-number}" -- cat inv.csv | pbcopy`, where `{environment}` is `production` or `tooling` and `container-number` is the number from the first step.

- Paste the contents in the spreadsheet by selecting the first cell in the first blank row following the manually maintained inventory items, then pasting with CTRL-Shift-V (Command-Shift-V for macOS) to paste without formatting. Then select the paste icon that appears and click `Split text to columns`

- [ ] Verify you have pasted the inventory for both production and tooling.
- [ ] Verify that the RDS information has not been overwritten.
