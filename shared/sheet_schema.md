# Application Log Schema

One Google Sheet titled `Construction Job Applications – [Student Name]` with three tabs.

## Tab 1: Applications

| Column | Notes |
|---|---|
| A — Date Applied | YYYY-MM-DD |
| B — Company | Tier 1/2/3 contractor or end-client |
| C — Job Title | exact title from JD |
| D — Role Type | Graduate / Placement / Internship / Trainee |
| E — Source Platform | Prospects, TARGETjobs, RateMyPlacement, LinkedIn, Indeed, Handshake, CareersinConstruction, University Careers, Direct, Other |
| F — Posting URL | **unique key for dedup** |
| G — Application Deadline | YYYY-MM-DD (CRITICAL — many grad schemes close before deadline) |
| H — Location | City / region |
| I — Salary | as posted, often "competitive" for grad roles |
| J — Sponsorship | Yes / No / Not stated |
| K — Fit Score | 0–100 |
| L — CV Version | filename of tailored CV |
| M — Cover Letter Version | filename |
| N — Status | Applied / Acknowledged / Online Test / Video Interview / Assessment Centre / Final Interview / Offer / Rejected / Withdrawn / Ghosted |
| O — Stage Date | YYYY-MM-DD of most recent stage |
| P — Online Test Score | if known |
| Q — Assessment Centre Date | YYYY-MM-DD if booked |
| R — Next Action | e.g. "Follow up 2026-05-13" or "Practice numerical tests by 2026-05-08" |
| S — Follow-up #1 Sent | YYYY-MM-DD or blank |
| T — Follow-up #2 Sent | YYYY-MM-DD or blank |
| U — Recruiter Contact | name + email if assigned |
| V — Notes | free text + drafted follow-up emails + interview reflection |

## Tab 2: Employer Research

Track companies you've researched even if you haven't applied yet. Saves duplicate research effort.

| Column | Notes |
|---|---|
| A — Company | |
| B — Tier | 1, 2, 3, or SME |
| C — Sectors | |
| D — Locations of interest | which UK offices or projects |
| E — Grad Scheme Open? | Yes / No / Date opens |
| F — Application Window | |
| G — Salary Reported | from RateMyPlacement / Glassdoor |
| H — Assessment Process | e.g. "online test → video → AC → final" |
| I — Sponsors visas? | Yes / No / Some roles |
| J — Notes | |

## Tab 3: Network Contacts

Build this gradually. Useful for grad scheme applications where alumni or recruiter contacts can give you an edge.

| Column | Notes |
|---|---|
| A — Name | |
| B — Role | |
| C — Company | |
| D — Connection | how you met / who introduced you |
| E — LinkedIn URL | |
| F — Email | |
| G — Last Contact Date | |
| H — Notes | what you've discussed, any commitments either way |

## Setting Up the Sheet

If creating fresh via Google Drive/Sheets:

1. Create new spreadsheet titled `Construction Job Applications – [Student Name]`
2. Rename Sheet1 to `Applications`, add headers, freeze row 1, freeze columns A-C
3. Add Sheet2 named `Employer Research`, Sheet3 named `Network Contacts`
4. Data validation:
   - Column D (Role Type) — dropdown: Graduate, Placement, Internship, Trainee
   - Column E (Source Platform) — dropdown of the 8 platforms + Other
   - Column N (Status) — dropdown of the status enum
   - Column J (Sponsorship) — dropdown: Yes / No / Not stated
5. Conditional formatting on Column N: Offer = green; Final Interview / AC / Video = blue; Rejected / Ghosted = grey; Applied / Acknowledged = yellow
6. Add a counter at the top: `=COUNTIF(N:N,"Applied")+COUNTIF(N:N,"Acknowledged")+COUNTIF(N:N,"Online Test")+COUNTIF(N:N,"Video Interview")+COUNTIF(N:N,"Assessment Centre")+COUNTIF(N:N,"Final Interview")` → "Active applications: X"
7. Highlight Column G (deadline) yellow if within 7 days, red if within 2 days, using conditional formatting on TODAY()

## Local Mirror

When Google Sheets isn't available, maintain the log as a CSV-formatted block in the chat. Output the new row plus a refreshed full table after every application.

## Duplicate Detection Logic

A job is a duplicate if any of:
1. Posting URL exact match against existing row
2. Company + Job Title + Role Type (case-insensitive, normalised whitespace) match within last 90 days

When a duplicate is detected, do not create a new row. Show the student the existing row and ask whether to re-tailor or skip.
