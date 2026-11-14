# School OS 5.3.14 — HR command centre

## A cohesive people workspace

The HR portal is reorganised around one **People & culture** workspace. Overview, Staff directory, Attendance, Leave, Queries and Payroll stay in a single navigation bar; More tools holds recruitment, induction, departments, contracts, allowances, payroll rules, duties, development, concerns and exit clearance. Existing workflows and permissions remain in place.

- Consistent glass panels, restrained teal accents, spacing, typography and borders across HR dashboards, profiles, tables and forms.
- Separate light/dark theme colours for headings, body text, muted text, fields and surfaces. The former pale heading on a white hero panel is removed. Primary and muted text tokens were checked above 4.5:1 against their intended solid surfaces in both themes; this is not a claim that every legacy screen has received a complete accessibility audit.
- Six attendance totals, a labelled donut/pie chart and a seven-calendar-day stacked distribution chart. These use actual school records and no external chart provider.
- A searchable daily attendance register. Summary cards open the corresponding named list; HR can open staff profiles or record attendance directly.
- A compact action queue for leave requests and open queries, plus a direct staff-directory link.
- Forms, menus and charts checked at 320, 390, 1024 and 1440 pixels. Glass panels retain solid-surface fallbacks.

[Light theme preview](SchoolOS_5.3.14_HR_Light.png) · [Dark theme preview](SchoolOS_5.3.14_HR_Dark.png)

## Automatic absence at midnight WAT

Attendance uses **Africa/Lagos (WAT)**, independently of the server's configured cron timezone.

- During the current day, staff without recorded attendance remain pending / not clocked in. Staff with no login are separately identifiable.
- When that day ends at **00:00 WAT**, missing attendance for active/exiting staff becomes absent. This applies to every calendar day, including weekends and holidays, as requested; no work-week or holiday exemption is assumed.
- Recorded presence/late attendance, approved leave, excused entries and verified HR attendance are retained. Payroll is not automatically reduced by attendance status.
- Staff without portal logins are included in day-close and can have attendance entered or corrected by HR, with a reason and history. Original clock times are retained.
- Approving leave after a day has closed replaces applicable automatic absences with leave. Manual HR decisions remain protected.
- Closing is school-scoped, serialized and repeat-safe. A second run does not duplicate or overwrite existing records. New employment still in induction, future start dates and already-exited staff without a captured entry are not assigned new automatic absences.
- The first run closes the previous calendar day. Older pre-update dates are not silently backfilled. From then on, quiet days are caught up in batches of up to 31 elapsed days per invocation.

### Processing without a scheduled worker

The rule is automatic when HR/attendance is accessed: the first request after midnight saves the closed day and catches up missed days. Open HR pages check for a changed WAT day every 30 seconds and refresh when there is no focused or edited POST form. Background browser throttling can delay this refresh. Unsaved forms are retained instead of being forcibly refreshed.

A PHP application cannot execute while the server receives no request and no scheduled process runs. For unattended persistence at midnight even when nobody is using the portal, use the included scheduled mode below. This distinction affects when rows are physically saved, not which calendar day is closed when the portal is next opened.

### Unattended worker for all schools

This release extends the existing CLI-only services worker with an **attendance-only** mode. It does not run external messaging/delivery jobs in this mode.

```sh
php /absolute/path/public_html/services_worker.php --hr-attendance --all-schools
```

For just one school:

```sh
php /absolute/path/public_html/services_worker.php --hr-attendance --tenant=1
```

In cPanel Cron Jobs, a once-per-minute schedule (`* * * * *`) with the all-schools command checks the WAT boundary and processes it within the next scheduled run. Use the hosting account's PHP CLI binary and real absolute path. No provider subscription or new service is required. Existing delivery-worker commands retain their previous behaviour.

The ZIP supplies and tests this mode; installing the update does not modify your hosting account's cron configuration. Running all-schools mode on a host with no HR employee records simply processes no schools. It is blocked over HTTP.

## Installation

1. Back up files and database, and test on staging.
2. Install **SchoolOS_5.3.14_HR_Command_Centre_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.14**, refresh HR tabs, and check both Light mode and Dark mode.
4. Check today's pending list and yesterday's absent/leave/present lists. Verify a staff profile and a manual correction.
5. If you need rows saved overnight without any portal visitors, configure the attendance-only cron command above.

This cumulative release includes previous staff profiles, queries/responses, direct chat, payroll, classroom, notification and mobile improvements. Existing accounts and saved media settings remain. No schema migration or provider setup is required; daily closure snapshots and correction history use existing private HR storage. The installer preserves configuration and provides file rollback. Rolling back files does not reverse already-recorded attendance or other business actions; take a database backup for that purpose.

## Retained data limits

Historical rosters before the first captured close still rely on the current employee register plus available attendance records; this is not a reconstruction of past headcount or account-link history. Closed snapshots preserve recorded employees when their employment stage later changes. Pre-update dates with missing records remain unknown, not inferred absence. Approved leave requires a linked account; unlinked staff can instead have an HR-verified leave/excused entry.

The profile's bounded record lists and approximately one-year attendance filter remain. The payroll engine still does not automatically prorate salary, accrue leave, file PAYE, remit pension or transfer money. The charts are an attendance overview, not a legal payroll-compliance certification.

[Validation report](SchoolOS_5.3.14_Validation.md)
