---
name: Run Pages ConMon Scans
title: "Run [month] [year] Pages ConMon scans"
about: INTERNAL ONLY schedule pages conmon runs
labels: compliance
assignees: ""
---

Re: [link to platform conmon ticket]

cloud.gov Pages also provides continuous monitoring artifacts. The process for creating them is detailed below. Current we only run ZAP Scans.

# ZAP Scans

From the [ZAP documentation](https://www.zaproxy.org/getting-started/): "Zed Attack Proxy (ZAP) is a free, open-source penetration testing tool being maintained under the umbrella of The Software Security Project (SSP). ZAP is designed specifically for testing web applications and is both flexible and extensible."

We run ZAP from a Pages operator's local machine. ZAP opens a Firefox instance that is configured to proxy all requests through ZAP. ZAP can then analyze and modify the requests.

## Preliminary work - Support User Setup

We scan our externally facing apps as _support users_ of cloud.gov Pages, via the cloud.gov IdP, instead of _admins_. This avoids issues with ZAP "clicking" on links with undesired impacts.

Each user should have a support user account created in the `zap-scans` organization prior to their first run.

## Install, Configure, and Update

- Check that you have the [latest stable version of ZAP](https://www.zaproxy.org/download/). Install/update via Homebrew with:
  - `brew update; brew install --cask zap` or
  - `brew update; brew reinstall zap`
  > NOTE: If you have used ZAP in the past on your workstation you may have an older version installed from when it was known as OWASP ZAP and distributed using the Homebrew formula `owasp-zip`. If you need to remove such an older Homebrew installation, run the following from the command line:
  - `brew uninstall owasp-zap`
  > NOTE: If you see an error running ZAP as an unsigned application, run the following from the command line:
  - `xattr -dr com.apple.quarantine '/Applications/ZAP.app'`
  - ZAP also has a [weekly build](https://www.zaproxy.org/download/#weekly) available. If the current stable build isn't working for some reason, try the weekly build instead. Download the ZIP, `cd` to it in your terminal, and run it with `./zap.sh`. If it outputs a message like `Exiting: ZAP requires a minimum of Java 11 to run`, run `brew install java` to install the latest Java and try again.
- Start ZAP and update
  - For "Session persistence", select "No, I do not want to persist my session..."
  - Use the Add-ons button in the toolbar to open "Manage add-ons". Check for available updates, and update all.
  - ZAP -> Settings -> Options:
    - Active Scan:
      - 3 hosts
      - 5 threads
    - JVM -> JVM options: `-Xmx8192m`
    - Network -> Global Exclusions:
      - Site - Firefox (select all)
      - Site - Font CDNs
      - Site - Mozilla CDN
    - Spider
      - Max Depth to Crawl: 5
      - Number of Threads: 7

### Quit and restart ZAP if you change the JVM options

- Be sure you have Firefox installed (with Homebrew `brew cask install firefox` or any way you chose). Chrome does not support proxy settings while Firefox does.

- `git clone git@github.com:cloud-gov/product.git` so you have the `context` files you need.

## Running the ZAP scans

Running the ZAP scan takes approximately one hour but can consume a large amount of system resources during the final step:

- From the cloud.gov `product` repo, load the cloud.gov `cloud.gov-conmon-pages.context` into ZAP (File > Import Context)
  - Delete the "Default Context" or any already completed context.
- On the top line of icons, there should be a Firefox icon on the far right. Click that to open Firefox preconfigured to proxy through ZAP.
- Open the `context` to see the included web applications (Context -> Included in Context)
- In the ZAP-configured Firefox, log in to each site in the context list.
> NOTE: These steps should start to populate ZAP's `Sites` list. If nothing is showing up there, you may need to disable Zscaler and try these steps again. `Sites` may not populate and the `Spider` scan may reported 0 URLs until Zscaler is disabled.
- To prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report), review the `Sites` list to ensure only the cloud.gov sites have a small red circle/sight on them (denoting the site will be included). Remove any sites not needed by CTRL-clicking on them and selecting `Delete`.
- CTRL-click on the context and run the `Spider` scan.
- After the `Spider` scan is complete, again CTRL-click on the context and this time run the `Active Scan`.
  - It is possible that this scan will pause at an arbitrary percentage complete (~72%) and fail to proceed. If you note no activity for at least 30 minutes, you can stop the scan here and proceed to the next step.
- After the Spider and Active scans are complete, export the results:
  - From `Report` menu, select `Generate Report ...`
    - Select the `Template` options, and use the templates:
      - Traditional HTML report
      - Traditional XML report
    - Name the files according to `YYYYMMDD-ZAP-pages.xml/html`. E.g.
      - 20210623-ZAP-pages.xml
      - 20210623-ZAP-pages.html
    - Optional: Check with compliance lead on whether we also need
      "Traditional HTML Report with Requests and Responses"

## Troubleshooting ZAP Scans

Ensure you are not running any other local webservers as the ports can infere with the scan.

If ZAP's `Sites` does not show the sites being visited, or if the scan operations do not seem to be successfully visiting sites, it may be necessary to disable Zscaler for the duration of the ConMon scan.

If a SecureAuth login loop occurs when trying to login to either of the production sites, it may be necessary to disable ZAP Firefox proxy settings prior to logging in by navigating to `Settings` -> `Network Settings` within Firefox and selecting the `No proxy` radio button . After successful authentication navigate back to `Network Settings` and select the `Manual proxy configuration` radio button. Reload both pages to update the site tree within ZAP.

If when you open ZAP's Firefox it fails to open displaying the "Explore your application with ZAP" landing page _even though you've stopped Zscaler..._ try rebooting. Sometimes it's time, and it works.

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

## Upload and wrap up

Upload all reports to Google Drive: https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U in a folder named `YYYYMMDD-ZAP-Nessus`.

You can shut down ZAP and Firefox.

## Acceptance criteria

- [ ] YYYYMMDD-ZAP-pages.xml ZAP scan is present in YYYYMMDD-ZAP-Nessus folder
- [ ] YYYYMMDD-ZAP-pages.html ZAP scan is present in YYYYMMDD-ZAP-Nessus folder
