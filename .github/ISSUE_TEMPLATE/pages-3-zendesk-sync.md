---
name: Run Pages/Zendesk user, role, and org sync
title: "Run [month] [year] Pages/Zendesk user, role, and org sync"
about: INTERNAL ONLY schedule pages/zendesk syncs
labels: ''
assignees: ''
---

Monthly review to make sure cloud.gov Pages users, orgs, and roles are accurately reflected in Zendesk.

# Pages/Zendesk user, role, and org sync

## Export organization, user, and role information from Pages Admin

- In Pages Admin, navigate to the Reports section
- View the Organizations report, and download a CSV export
- View the Users report, and download a CSV export

## Prepare and import CSV data into Zendesk

### Organization Import

*Important! The Organizations report needs to be imported first otherwise users being added in the Users report to new organizations which don't yet exist in Zendesk will cause the job to fail*

- Download and open the CSV export in Google Sheets for editing purposes
- In the header of the first column rename "Organizations" to "names" 
- In the header of the second column rename "Agency" to "details"
- Save the sheet as an CSV
- Navigate to the Zendesk admin center 
- In the lefthand panel locate "Bulk actions" and choose "Import organizations"
- An import job report will be sent to your .gov inbox where you can view if the job was successful/unsuccesful

### User Import

- Download and Import the Users CSV into Google Sheets for editing purposes
- For "Seperator type" keep it unchanged from "Detect automatically" 
- Delete the columns "Created" and "Last Signed In"
- Delete all of the content in "ID"
- The remaining columns should be "ID", "Email", "Organizations" and "Details"
*The "Name" and "Email" fields are required for importing new users, without them the entire job will fail*

- Copy and paste the entire "Email" column into the blank column (A)
- Rename the header to "Name" from "Email"
- Utilize the "Find and replace" function by hitting command + shift + H
- In search choose "Specific range" from the dropdown and specify A:A as the range parameter
- In "Find" specify all email addresses that need to be replaced and leave "Replaced with" null
(i.e. Find: "@gsa.gov" Replace with: "")
- This will remove all the email address from the names under the "Name" header making it easier to format for importing purposes
- Replace all "." with an " ," — that is, a space then a comma
(i.e. from "pages.user" to "pages, user")
- Save the sheet as a CSV
- Navigate to the Zendesk admin center 
- In the lefthand panel locate "Bulk actions" and choose "Import organizations"
- An import job report will be sent to your .gov inbox where you can view if the job was successful/unsuccessful

**Note** In the CSV you will notice a number of users' emails towards the bottom which do not have the organization or details field associated with them and will consequently result as failures in the report results. For example:

```"X users failed","Error message"
"Unknown row descriptor","Name:  is too short (minimum one character)"  
```
This can be disregarded.

## Acceptance criteria

- [ ] Orgs in Zendesk match current Pages orgs
- [ ] Org users in Zendesk match current Pages partners users, including
  - [ ] Org assignments
  - [ ] Roles (org manager or not)
  - [ ] Names and emails 
