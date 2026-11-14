# School OS 5.3.13 validation

Local tests on 14 November 2026 using synthetic school accounts and data. No production staff records were accessed.

## Attendance, query and privacy tests

- Passed: Missing clock-ins, verified absence, leave and unlinked staff remain distinct
- Passed: HR can correct attendance with a reason without losing clock times
- Passed: Non-HR actors, cross-school records, future dates and dates before appointment are rejected
- Passed: HR issues a private query and only the linked staff member may respond
- Passed: Query notifications are scoped to staff and authorised HR
- Passed: Only HR closes a query with an outcome; closed records cannot be edited
- Passed: Staff profile includes history and pay but hides unpublished appraisals from the staff member
- Passed: New overview, date log, staff profile and query views render without warnings

## Retained HR register/payroll-rule tests

- Passed: One transaction creates staff, private profile and four induction tasks
- Passed: Employment cannot activate with incomplete induction
- Passed: Editing a profile preserves salary and saves contact information
- Passed: Non-HR staff cannot create or edit another staff record or read private profile
- Passed: Invalid links and duplicate portal links are rejected
- Passed: Failed staff creation leaves no orphan directory entry
- Passed: Completed induction permits activation
- Passed: Every HR tab renders for HR manager and employee without PHP warnings
- Passed: Account link removal requires confirmation and omitted fields preserve links
- Passed: Open-ended permanent appointment is accepted; reversed dates are rejected
- Passed: Ordinary tax-band rows save the same validated payroll rules as legacy input

## Browser workflows

- Passed: HR overview charts and date filtering
- Passed: Register opens a complete linked staff profile
- Passed: Profile chat opens the correct permitted staff conversation
- Passed: HR issue → staff response → HR outcome, with profile and self-service context preserved
- Passed: Overview, date log and full staff profile fit 320px and 390px screens

## Installer

- Passed: Existing 5.3.12 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.13 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.12 metadata
- Passed: Traversal entries are refused before file changes

623 page visits across 14 synthetic roles passed without HTTP/PHP rendering failures. Changed PHP and JavaScript syntax passed. Browser tests use independent HR and staff sessions, verify the real query forms and redirects, open the correct staff conversation, and check overview/log/profile layouts at 320px and 390px. Attendance corrections preserve original times and create a reasoned history item. Server checks distinguish absence from missing clock-ins, deny cross-school/private-record access and prevent responding after query closure.

Package verification checks every file against the SHA-256 manifest and confirms installation, injected-failure recovery, duplicate-version refusal, rollback and traversal rejection. Configuration, credentials, database files and local tests are excluded from the package. Actual school-device and attendance-policy acceptance should be performed after installation. Historical roster and calendar limitations are documented in the guide; no automatic absence or payroll-compliance claim is made.
