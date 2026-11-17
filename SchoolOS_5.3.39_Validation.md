# SchoolOS 5.3.39 — Validation

Local checks used PHP 8.4, MariaDB, requests, Chromium and Playwright with synthetic schools and an actual isolated demo database. No hosted school was deployed or used as a test database.

| Check group | Passed | Failed |
|---|---:|---:|
| Staff provisioning and role/access scenarios | 38 | 0 |
| Dashboard/browser scenarios, including all 29 profile entry points and all 35 demo logins | 31 | 0 |
| Role-responsive layouts and usable form scenarios | 31 | 0 |
| Full isolated-demo dashboard renders with SQL/type-error detection | 35 | 0 |
| Demo seeding, ownership boundaries and additive/idempotent upgrade | 3 | 0 |
| Fresh mixed-collation demo with connected support/timetable examples | 1 | 0 |
| Core role workflow scenarios | 15 | 0 |
| Additional connected workflow/scope scenarios | 6 | 0 |
| Actual bearer API routing/revocation and school-brand contrast | 2 | 0 |
| Public family registration/browser scenarios | 5 | 0 |
| Login demo-search contrast/filtering in both themes | 2 | 0 |
| Missing optional-module preparation state | 1 | 0 |
| Incomplete branding school-identity fallback | 1 | 0 |
| Fourteen-role read-only route smoke checks | 739 | 0 |
| Existing 5.3.38 updater install/recovery/rollback | 5 | 0 |
| PHP syntax | 42 | 0 |

Both changed JavaScript files passed node --check. The final ZIP is checked against its manifest and current source; it contains 41 approved files plus release.json.

## Working flows exercised

The 29 profiles were created with exact permission sets and connected employment. Each signed in with a school ID, completed its initial password change and opened its assigned tools. The 27 Staff-type overviews were checked at phone and desktop widths, with status pies and actual-record charts. Website fields, report columns and integration scopes were exercised through the browser; the report flow generated and downloaded an actual private CSV.

The 35 demo choices were signed into the marked isolated sandbox. Full role renders separately reject hidden SQL/type errors, rather than counting an HTTP 200 response as success. Fresh and existing demo paths were checked with different database collations. Live-account passwords/configuration were not copied into the demo, and upgrade preserves existing demo account passwords.

Workflow tests cover website creation/submission/independent publication; employee purchasing and independent review; asset care; school curricula, approved report formats/calendar and class policy; selected-period timetable generation, independent approval and one-time application; finance-only/HR-only reports and private exports; privacy requests and reviewed responses; consented adult alumni and supervised mentoring requests; evidence-backed school deadlines; independently approved, expiring read-only integration tokens; scoped school-group reporting; evidence-based pupil support review; approved regular-collector handover; and guardian-controlled prepaid purchases after independent bank verification.

Connected tests create an actual driver/vehicle/route/pupil manifest and start its trip; connect a hostel/warden/bed/pupil allocation; approve a communication flow without creating unsolicited deliveries; reject unauthorized integration scopes and revoked reporting access; classify expired collection credentials accurately; and reject foreign subjects/unlisted report columns.

API checks call the actual HTTP bearer endpoint, receive permitted aggregate data, and reject an unauthorized dataset and revoked token. School-brand text selection is checked against WCAG 4.5:1 contrast for light, dark and mid-tone colours. This is a colour-specific check, not a full accessibility certification.

## Family registration

Browser checks cover new root-based and legacy links, actual school identity/contact details, 360px/1440px layouts in both themes, validation between steps, siblings, retaining entered values, safely rendered review text, pending submission and private progress links. Submission created two child-review rows and no new user accounts. Access with an incorrect private key was refused. The fictional preview accepts only GET/HEAD and refuses POST with HTTP 405.

The form still uses the existing school verification and approval handlers. No test sent a real email, SMS, WhatsApp message, payment or media connection. External delivery, real bank receipts, hosted DNS/TLS, provider capacity and live-school operational policies require school-side verification.

## Installation and cleanup

The unchanged 5.3.38 updater passed injected mid-install failure recovery, complete file/hash installation with configuration preserved, same-version refusal, explicit prior-file/version rollback and ZIP traversal rejection.

Fixtures are confined to two synthetic ordinary-school tenants and marked local demo databases. Temporary local demo/canonical-address settings are restored after verification. Configuration, keys, credentials, test data and scripts are excluded from the ZIP.

These results validate the changed entry points and selected real workflows locally. They do not certify every possible application state, historical data or the hosted school's production configuration.
