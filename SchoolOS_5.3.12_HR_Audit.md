# School OS 5.3.12 — HR audit and validation

Reviewed source and synthetic local workflows on 14 November 2026. No production database or employee data was accessed.

## Findings and disposition

| Finding | Change / outcome |
| --- | --- |
| Three separate staff creation/linking forms; unexplained legacy department | One Add staff member workflow; separate existing-directory import |
| Account edit starts at No account; raw IDs in register | Prefilled selected employee editor, named department/login, confirmation before unlinking |
| Missing structured appointment/contact/qualification record | Private employee profile fields, appointment category/type and optional contact/emergency/qualification information |
| Activation could have no induction checklist | Four tasks seeded for new staff/hired applicants; at least one completed checklist required for activation |
| Permanent appointment forced to have an end date | Optional contract end; duties still require a valid ending time |
| Raw kobo, basis points and JSON in payroll screens | Naira and percentages, editable validated band rows, saved rules prefilled |
| Numeric IDs required for review actions | Named selectors for HR items, applications, allowances, leave, advances and payroll months |
| Payment controls shown to HR accounts that cannot pay | Controls match school administrator permission; backend checks retained |
| Large unstructured navigation and generic notes prompt | Four task groups, contextual guidance and record-specific wording |
| Overlapping leave requests allowed | Pending/approved date overlap blocked |
| Narrow display overflow | HR forms tested at 320/390px; compact top-bar wrapping corrected |

The available modules cover a useful school HR core: staff register, recruitment, induction/safeguarding checklist, appointments, departments, attendance, leave approvals, supervision/cover duties, pay/allowances, reviewed tax/pension settings, payroll/payslips, advances, appraisals, CPD, confidential concerns and exit clearance. Their presence does not imply automatic leave accrual, statutory filing or bank payments. Remaining manual processes are documented in the installation guide and relevant screens.

## Local automated validation

### HR server

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

### Browser

- Passed: Staff register and prefilled edit links
- Passed: Editable tax-band rows replace raw JSON
- Passed: HR forms fit 320px and 390px mobile screens

### Installer

- Passed: Existing 5.3.11 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.12 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.11 metadata
- Passed: Traversal entries are refused before file changes

611 role-page visits across 14 synthetic roles returned without HTTP/PHP rendering errors. Changed PHP and JavaScript syntax passed. Every packaged file has a SHA-256 manifest entry; config, credentials, local tests and database files are excluded. Browser layout checks include the register, payroll rules, induction and advance screens at 320px and 390px. Payroll rule validation checks equivalence with the existing engine; this release does not change statutory assumptions or certify payroll law compliance.
