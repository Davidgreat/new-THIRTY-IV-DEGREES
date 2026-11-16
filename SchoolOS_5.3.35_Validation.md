# School OS 5.3.35 — Validation

Local validation on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright with fictional school records.

| Check group | Passed | Failed |
|---|---:|---:|
| School-led registration/access server checks | 23 | 0 |
| Account/password and schema-preservation checks | 4 | 0 |
| Raw-link and isolated-demo compatibility boundaries | 3 | 0 |
| Existing application/offer/enrollment regression | 20 | 0 |
| Full admissions/family/student browser journeys | 12 | 0 |
| Staff credential issuance, route protection and theme captures | 4 | 0 |
| Actual expired-credential HTTP login | 1 | 0 |
| Pupil/document and closed-draft HTTP history checks | 2 | 0 |
| Page regression across 14 roles | 727 | 0 |
| Existing-updater installation and rollback | 5 | 0 |
| PHP syntax | 42 | 0 |

The changed JavaScript also passed `node --check`.

## Behavior exercised

- Save a phone-first, no-email pupil draft without activating a pupil/login or creating financial/service records.
- Repeat a draft submission or admission without creating duplicate pupils; reject a reused admission number; require review of possible identity matches.
- Confirm a school-office admission without fabricating a public application, offer, test or payment.
- Upload/download a private PDF through the browser, block admission pending review and carry verified copies into pupil documents.
- Prepare parent access without granting admissions default issuance authority; approve through the school administrator and display a credential once.
- Sign in by school ID, change the temporary password and reach the correct parent and student dashboards.
- Add a verified sibling to the same parent account without resetting its password; connect a second guardian using searchable existing-account selection.
- Preserve first-password-change/expiry and verified recovery for school IDs without contact email. Reject expired credentials through the actual HTTP login screen.
- Refuse cross-school classes/pupils/accounts, elevated account roles, revoked staff, parents/teachers attempting admissions writes and invalid CSRF tokens.
- Import CSV drafts transactionally, retry the same import safely and roll back every row on invalid data.
- Allow explicit school-admin delegation/revocation of family approval; keep generic raw family linking out of the bypass path.
- Connect office-admission parents to admissions chat and their own children while retaining student contact restrictions.
- Render the main admissions pages at 1440px and 360px in both themes without horizontal overflow or captured browser/PHP errors. Retain personal welcome and decorative scene.
- Check all 14 existing role homes and reachable working pages: 727 HTTP/page checks, zero failures. This exposed and fixed dashboard pagination being treated as a public website `page` parameter.

The existing 20-check application regression suite retained its behavioral assertions; its footer-version expectation was updated from 5.3.28 to 5.3.35. Tests cover offers/acceptance, payment checks, snapshots, document replacements, enrollment rollback, account/class mismatches, idempotency, family tokens, entrance assessments and chat scope.

## Package and updater

The final cumulative archive contains 36 approved application files plus `release.json`. Every archive file matches its manifest SHA-256 and current source. Configuration, credentials, test helpers and fictional fixture data are excluded.

A separate 5.3.34 installation copy used its existing updater. All five checks passed: recovery after injected mid-install failure; complete installation with matching hashes/journal and unchanged configuration; rejection of reinstalling the same version; explicit prior-file/version rollback; and traversal rejection before mutation.

Database preparation adds tables without deleting existing pupils or accounts; repeated preparation preserved counts. File rollback is not a database rollback. School-ID-only accounts need the new authentication code, so access must be planned when reverting to an older version.

## Boundaries

These results are local verification, not a production certification or a test of the hosted school's current database/settings. No live payment, SMS/email delivery or hosted deployment was performed. Dedicated isolated-demo behavior was checked at its schema-admission boundary; the user's configured remote sandbox was not available for an end-to-end refresh test. Existing unexpected-schema refusal remains in place.

Source changes relative to 5.3.34: `experience_ui.php`, `index.php`, `experience.php`, `experience_admin.php`, `portal_experience.php`, `portal_collaboration.php`, `portal_experience.css`, `portal_experience.js`, `VERSION.txt`; updated existing dependencies `experience_demo.php` and `affiliate.php` are included in this cumulative archive.
