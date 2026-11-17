# SchoolOS 5.4.1 validation

Tested locally with synthetic MariaDB school tenants, an ownership-marked isolated demo database, actual HTTP requests and Chromium. No hosted installation, real bank transfer, live SMTP delivery or production database access was performed.

## Permission and record checks

- Class, branch and department scope checks, including cross-school record ID refusal and unsupported scope rejection.
- Multiple responsibilities on one employee account, including a teacher with academic leadership and examination responsibilities and an admissions identity with a reviewed library responsibility.
- Individual permission restrictions, template changes, template disable/re-enable, assignment revocation, changed approval ceilings, inactive accounts and stale identity refusal. Injected audit-write failure rolls back the permission change atomically.
- Distinction between report viewing, export and money-processing authority. Scheduled-worker exports recheck export permission.
- Creation of all six new specialist profiles through the actual Staff & access action, including HR links, working modular assignments and matching temporary credentials.
- New single-owner school setup enables a small starting service selection without creating unwanted employee accounts; another school’s preparation does not mark it prepared.

## Working records

- Examination class time conflicts, shared mark moderation, refusal of own-score approval and actual term publication into the existing academic record.
- Encrypted counselling notes, appointment overlap refusal, cross-role and cross-school access refusal, follow-up version checks.
- Visitor check-out, review plans and independent reviewer assignment, department-linked staff review records, completed-record archive and retained history. Only the assigned reviewer can submit findings; coordinator closure requires that submission and a different actor; the reviewer cannot reopen a closed review.
- Shared-ledger invoice creation, balanced journal entries, pending payment reconciliation, independent approval, per-transaction ceiling rejection, refund settlement and recomputed family invoice balance.
- Verified parent/staff chat permission within pupil scope and authenticated pupil search. Invalid CSRF and unrelated permission lookups are rejected or return no permitted results.
- Scoped pupil lookup with 1,500 unrelated pupil records still returns only the permitted pupil; local query time was approximately 0.002 seconds. This is a local check, not a production performance guarantee.

## Browser and upgrade checks

- All 41 isolated demo picker logins reach their dashboards.
- School Admin service, template, employee, branch and audit screens at 360px and 1440px; new principal, examination, counselling, security, accounts and review workspaces at mobile width. Checked document overflow and JavaScript errors.
- Search-and-select pupil invoice creation through the actual browser form. Read-only legacy book mutation refused by the server; unavailable write forms and revoked base-duty menus are hidden in the browser.
- Actual legacy 35-account sandbox without modular tables upgrades to 41 accounts, preserving teacher password hash and ended employment history. New role assignments and the sandbox table inventory are prepared.
- First real web demo login performs role preparation before authentication without relying on a CLI pre-upgrade. The previous missing-helper loading-order failure is covered.
- All 42 application PHP files pass syntax checks.
- Original 5.3.40 updater installs the cumulative 41-file package with matching manifest hashes and unchanged configuration. Injected mid-install failure rolls back; explicit rollback restores old files and metadata; same-version and traversal packages are refused.

## Deliberate boundaries

Legacy school-wide operational workspaces require school-wide grants. Narrower class/branch scope is implemented for the new record-scoped workspaces; department scope applies to staff reviews. Unsupported scope combinations are refused. Teaching assignments, family links, driver routes, protected approval rules and separate school-group consent remain enforced.

Counselling export requires its own permission. Viewing data in a web browser cannot prevent a user from photographing or manually copying information they are authorised to see. Financial confirmations record independently verified events and do not themselves move money. School Admin authority remains distinct from a configurable employee responsibility.

The 5.4.1 updater additionally refuses a file-only downgrade below 5.4.1 after any school has prepared modular access, fails closed if the database check is unavailable, and allows recovery when the matching older database state is present. These cases were tested against installed package hashes and version metadata.
