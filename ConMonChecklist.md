# Continuous Monitoring Checklist

## Instructions

After delivery of a monthly ConMon report:

1. Create a new issue in `cg-product` called "Deliver ConMon report for [due date]"
1. View the raw source of this file
1. Copy everything below the line into the new issue's body
1. Replace [due date] in title and body with the next due date
1. Assign the issue to a member of the HighBar squad, add the HighBar label, and add it to the FedRAMP-related-work epic for that quarter
1. Submit the issue
1. Put the issue into the "Ready" pipeline in ZenHub

---

In order for us to update the JAB on our compliance in a consistent way, we need to deliver a Continuous Monitoring report on [due date].

**Implementation sketch**

A week before [due date]:

* We ran OWASP ZAP on the following (using [these manual scanning instructions](https://pages.18f.gov/before-you-ship/security/dynamic-scanning/#manual-scanning), authenticated, passive) and uploaded the fresh results to [a folder in this folder](https://drive.google.com/drive/u/0/folders/0B5fn0WMJaYDnaFdCak5WNWRGb1U):
	- [ ] https://ci.fr.cloud.gov/ (ci.xml)
	- [ ] https://community.fr.cloud.gov/ (community.xml)	
	- [ ] https://dashboard.fr.cloud.gov/ (dashboard.xml)
	- [ ] https://invite.fr.cloud.gov/ (invite.xml)
	- [ ] https://landing.fr.cloud.gov/ (landing.xml)
	- [ ] https://login.fr.cloud.gov/ (login.xml)
	- [ ] https://logs.fr.cloud.gov/ (logs.xml)
	- [ ] https://metrics.fr.cloud.gov/ (metrics.xml)

- [ ] We've grabbed a fresh set of Nessus scans from https://nessus.fr.cloud.gov/

* We've updated [our Google Drive POA&M right here](https://docs.google.com/spreadsheets/d/16igVl8cD3SqeX5_SOn5Su34KmwMRnP20gPbfQlqIwfM/edit#gid=1701775784):
	- [ ] We've updated all columns to include the most recent info about remediations, milestones, statuses, etc., including updating the status date column.
	- [ ] We've moved any web scanner items that should be moved to closed (in other words, items originally found by a scanner where we have new scans that prove these things are fixed).
	- [ ] Any new identified web or OS vulnerabilities are listed.

**Acceptance criteria**

- [ ] We've emailed our PMO an exported copy of our draft POA&M, new web scans, and new OS scans by COB on [4 work days before the due date]
* We've done the following by COB on [1 work day before the due date]:
	-  [ ] Uploaded our POA&M to [this folder](https://community.max.gov/pages/viewpage.action?pageId=1034682621)
	-  [ ] Uploaded our web scans to [this folder](https://community.max.gov/display/FedRAMPExternal/GSA+18F+Cloud.gov+Web+Scans)
	-  [ ] Uploaded our OS scans to [this folder](https://community.max.gov/pages/viewpage.action?pageId=1034682662)
	-  [ ] Emailed our PMO to let them know that's done
