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

*Important! The Organinzations report needs to be imported first otherwise users being added in the Users report to new organizations which don't yet exist in Zendesk will cause the job to fail*

- Download and open the CSV export in Google Sheets for editing purposes
- In the header of the first column rename "Organizations" to "names" 
- In the header of the second column rename "Agency" to "details"
- Save the sheet as an CSV
- Navigate to the Zendesk admin center 
- In the lefthand panel locate "Bulk actions" and choose "Import organizations"
- An import job report will be sent to your .gov inbox where you can view if the job was successful/unsuccesful

### User Import

- Download and open the CSV export in Google Sheets for editing purposes
- Delete all columns besides "Email" "Organizations" "Name" "Details"
*The "Name" and "Email" fields are required for importing new users, without them the entire job will fail*
- Save the sheet as an CSV
- Navigate to the Zendesk admin center 
- In the lefthand panel locate "Bulk actions" and choose "Import organizations"
- An import job report will be sent to your .gov inbox where you can view if the job was successful/unsuccesful

## Acceptance criteria

- [ ] Orgs in Zendesk match current Pages orgs
- [ ] Org users in Zendesk match current Pages partners users, including
  - [ ] Org assignments
  - [ ] Roles (org manager or not)
  - [ ] Names and emails 
