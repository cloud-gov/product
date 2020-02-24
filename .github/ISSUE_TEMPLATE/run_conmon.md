## Run [month] [year] ConMon scans

In order for us to update the JAB on our compliance in a consistent way, we need to run Continuous Monitoring scans on approximately the 23rd of the month. (If this date falls on a weekend or federal holiday, adjust to the last business day before the date.)

For context, see our [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), including [the monthly reporting summary explanation](https://cloud.gov/docs/ops/continuous-monitoring/#monthly-reporting-summary). 

Check that you have the [latest stable version of ZAP](https://github.com/zaproxy/zaproxy/wiki/Downloads).

- [ ] We ran OWASP ZAP on the following domains using steps #1-6 of the manual scanning instructions at https://before-you-ship.18f.gov/security/dynamic-scanning/#scanning - spider and active after getting authenticated through the browser:
```
https://ci.fr.cloud.gov/
https://dashboard.fr.cloud.gov/
http://dashboard-beta.fr.cloud.gov/
https://account.fr.cloud.gov/
https://cloud.gov/
https://idp.fr.cloud.gov/
https://login.fr.cloud.gov/
https://opslogin.fr.cloud.gov/login
https://logs.fr.cloud.gov/
https://admin.fr.cloud.gov/
https://prometheus.fr.cloud.gov/ 
https://grafana.fr.cloud.gov/
https://alertmanager.fr.cloud.gov/
https://logs-platform.fr.cloud.gov/
```
  - Load the [cloud.gov conmon](https://raw.githubusercontent.com/18F/cg-product/master/cloud.gov-conmon.context) ZAP context from this repository.
    - Check the context file to see if it needs updating (update if necessary).
  - You have to log in so that ZAP can scan inside the authenticated websites, which includes being on the VPN.
  - Make sure to scan _only_ those sites, rather than browsing other URLs while ZAP is running, to prevent getting noise in the scan results (since that causes major confusion when the FedRAMP team processes the ConMon report).

- [ ] We exported and uploaded those fresh OWASP ZAP results in XML format to a folder in the folder at https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U
- [ ] We also grabbed the OWASP ZAP scans in human-readable HTML format and uploaded them to that folder.
- [ ] We grabbed a fresh set of Nessus scans (both OS and database/RDS; grab all scans except staging) from https://nessus.fr.cloud.gov/ in .nessus format and uploaded the fresh results to a folder in the folder at https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U - requires auth (Cloud Ops or Deputy Director).
- [ ] We also grabbed the Nessus HTML export - https://docs.tenable.com/nessus/6_8/Content/Exported_Results.htm - for those scans and uploaded them to that folder.
- [ ] We updated the [POAM Inventory sheet](https://docs.google.com/spreadsheets/d/1_9Neq8fGO4NdQhsqLXDn445g3GUa1k_FZUrUXc7hulY/edit#gid=1371600163) that's in the [same folder](https://drive.google.com/drive/folders/0BynIxtx-CfkdcjVfTlkxZ3FQWjg) as the POAMs. From tooling and production BOSH, run `python generate-POAM-inventory.py`


1. Open the Google sheet, paste the output from the above command, replacing the existing contents
1. Click the Paste icon that pops up after you paste.
1. Click Split text to columns.
