---
name: Export Pages orgs/published sites to billing sheet
title: "Run [month] [year] Pages orgs with published sites export to billing sheet"
about: INTERNAL ONLY schedule Pages orgs with published sites export to billing sheet
labels: ''
assignees: ''
---

Monthly export of orgs with published sites to billing sheet.

# Pages orgs/published sites export to billing sheet

## Export orgs with published sites from Pages Admin

- In Pages Admin, navigate to the Reports section
- View the Organizations With Published Sites report, and download a CSV export

## Import orgs with published sites into billing sheet

- Open the current cloud.gov billing sheet in Google Sheets
- Switch to the tab "Pages Published Orgs"
- In the Google Sheets file menu, choose "Import"
- In the Import File dialog, choose "Upload"
  - Drag in or browse to select the CSV export generated from the report in the section above
  - For Import Location choose "Replace current sheet"
  - For Seperator Type choose "Comma"
  - Leave the checkbox checked next to "Convert text to numbers, dates, and formulas"
  - Press the "Import data" button

## Acceptance criteria

- [ ] Current export generated of orgs with published sites
- [ ] Orgs with published sites imported into billing sheet
