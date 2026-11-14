# School OS downloads

## Latest: 5.3.14 — HR command centre

[Download the installable update](SchoolOS_5.3.14_HR_Command_Centre_Update.zip?raw=true)

[Installation and attendance guide](SchoolOS_5.3.14_README.md) · [Validation report](SchoolOS_5.3.14_Validation.md)

A unified People & culture workspace with glass panels, readable light/dark themes, one navigation bar, a donut chart, a seven-day stacked chart, a searchable daily register and a compact action queue. Existing staff profiles, queries, chat and payroll remain connected.

Missing attendance now closes as absent at the WAT day boundary. Existing presence, approved leave and excused/manual entries are preserved. HR can record attendance for staff without logins too. Today remains pending until midnight; every calendar day is included. Older dates before initial activation are not silently backfilled.

Day-close saves automatically on the next HR/attendance request and catches up quiet days. For unattended overnight processing with no visitors, the included CLI-only attendance mode can run from cPanel cron for all schools. The guide gives the command; the hosting scheduler has not been configured by this ZIP.

Install through **Platform Super Admin → Updates & Plugins → Core updates**, confirm **5.3.14**, then refresh HR tabs. Back up files and database first. No schema migration or external provider is required.

[Light theme preview](SchoolOS_5.3.14_HR_Light.png) · [Dark theme preview](SchoolOS_5.3.14_HR_Dark.png)

Validated: six day-close scenarios, eight HR/privacy scenarios, five browser workflows, two design/search checks, 625 role-page requests and five installer/rollback scenarios.

SHA-256: `238e56b6f6bebf6372f36f625aedc8c76315580f1e16de2b42ef60aeee3208cf`

## Earlier releases

[5.3.13 staff profiles](SchoolOS_5.3.13_README.md) · [5.3.12 HR register/payroll](SchoolOS_5.3.12_README.md) · [5.3.11 typing reliability](SchoolOS_5.3.11_README.md) · [5.3.10 emojis/reactions](SchoolOS_5.3.10_README.md) · [5.3.9 social chat](SchoolOS_5.3.9_README.md) · [5.3.4 Learning Studio](SchoolOS_5.3.4_README.md)
