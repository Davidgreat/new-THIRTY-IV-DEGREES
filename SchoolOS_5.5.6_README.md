# SchoolOS 5.5.6 — Platform people & capacity

## Install
Keep a current backup, then sign in with the real Platform Super Admin account. Open Updates & Plugins, upload **SchoolOS_5.5.6_Platform_People_and_Capacity_Update.zip**, tick the trusted-source box and choose Verify & Install Update.

After installation, open **People & capacity** in the Super Admin sidebar. Four people counters also appear on the platform Overview. With clean links, the dedicated page is `/platform-control/people`; the legacy address is `/index.php?s=platform&view=people`.

The update contains 44 approved application files, a release manifest and verified hashes. It preserves the document-design and ROI updates. No configuration, private keys, test data or SQL migration is included. This reporting feature does not edit school, student, staff, payment or user records. Installation and rollback are tested with the 5.5.5 updater.

## Included
- Total registered student records, plus the active-student count.
- Parent accounts and school staff accounts, including teachers and school administrators.
- All registered user accounts across schools, platform operations and partners, including disabled accounts.
- Separate enabled/disabled school and platform account totals.
- Schools with the highest and lowest student counts, with ties handled explicitly.
- Empty-school count and the smallest school that has students.
- Account-distribution donut and top-schools chart.
- Searchable, sortable and paginated school breakdown, with school names/IDs and student, parent, staff and account counts.
- CSV export of all matching schools, independent of the current page; no individual student names, emails or phone numbers.
- Aggregate records that reference a missing school are flagged rather than silently assigned to another school or discarded.
- Responsive light/dark layouts and updated platform/user guides.

## What the totals mean
Student records and login accounts are different measures. A school may register a pupil before creating a student login. A parent with several children counts once per parent login. A staff member with several job assignments counts once per staff login. Staff counts include teachers, admissions, school administrators and other school work accounts; contact/personnel records without logins are not added to account totals. The total-user counter counts each saved login once and does not add student records on top of student logins.

These are record/account counts, not a verified count of unique individuals across different schools. Retained archived students and disabled accounts still use storage, so they remain visible in registered totals. Active students follow saved school status; legacy student records with no status are treated as active. All schools are included, regardless of subscription status. The separately configured demo database does not inflate production totals.

## Refresh, filters and access
Open the page or select Refresh counts to read current saved records. School search, sorting and pagination change the table; they do not replace platform-wide totals. Highest/lowest rankings use all registered student records. The lowest ranking includes empty schools, with a separate non-empty comparison for context. CSV uses the current school/search/sort filters and contains all matching rows.

Only a current active Platform Super Admin can access these global reports or exports. Delegated platform staff do not receive the new page merely because they can view assigned schools or platform finances. School admins and families do not gain cross-school visibility.

## Infrastructure planning
Use these counts to understand stored records and account capacity. They do not directly measure simultaneous sessions, CPU, RAM, database size, media traffic or bandwidth. Use hosting telemetry and load tests alongside them when deciding when and how to scale.

## Validation
Local synthetic-data tests cover count reconciliation, account/record distinctions, disabled and archived entries, missing-school exceptions, tied rankings, zero-student schools, literal wildcard search, safe sorting, pagination, immediate saved-record updates, account scope, CSV downloads and spreadsheet-safe names, mobile/desktop layouts, clean subfolder links, update installation and rollback. Preview screenshots contain fictional test schools and counts, not production traction.
