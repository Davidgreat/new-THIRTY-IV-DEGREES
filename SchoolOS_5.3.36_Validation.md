# School OS 5.3.36 — Validation

Local verification in November 2026 using PHP 8.4, MariaDB, Chromium/Playwright and fictional school records.

| Check group | Passed | Failed |
|---|---:|---:|
| Family submission, approval, security, tokens and delivery logic | 21 | 0 |
| Batch rollback, recovery, pending accounts, role/email reuse and compatibility | 8 | 0 |
| Full family-onboarding browser journeys | 10 | 0 |
| Correction/recovery and malformed-input browser checks | 3 | 0 |
| Existing school-office registration regression | 23 | 0 |
| Existing application/offer/enrollment regression | 20 | 0 |
| TLS/STARTTLS SMTP outcomes and header-injection refusal | 5 | 0 |
| Shared-demo external-action boundaries | 3 | 0 |
| Reachable pages across 14 existing roles | 735 | 0 |
| Existing-updater installation and rollback | 5 | 0 |
| PHP syntax | 42 | 0 |

The changed JavaScript passed node --check. Four isolated local SMTP protocol transcripts additionally verified the complete UTF-8 body and encoded subject over SSL/TLS or STARTTLS with a locally trusted test certificate.

Browser tests exercised multi-child public submission, private receipts, office entry, existing-record matching, reviewed sibling approval, failure reporting, parent password setup and access to both children, parent-assisted student setup, WhatsApp redirect construction, requested corrections and replacement private links. Phone/desktop and light/dark views passed overflow and captured-error checks.

Server checks cover pending-only submissions; repeat protection; scoped matching/approval; no financial or optional-service fabrication; old-password preservation; hashed/protected single-use tokens; expired/replayed/recovery-invalidated token refusal; stale-review rejection; guardian/contact verification; atomic batch failure; pending versus deliberately disabled accounts; encrypted school SMTP; scoped notifications; and staff who also need separate parent access.

SMTP tests used only a fake service on the local machine. They exercised acceptance, rejection and connection loss after DATA. Closing after successful acceptance does not cause a retry because QUIT failed. Uncertain outcomes remain distinct, and header injection is refused before connection. No real parent mailbox or actual SMTP credential was used.

All 735 page checks across platform admin, school admin, admissions, teacher, parent, student, partner, HR, driver, warden, librarian, store, communications and reviewer passed. Existing registration and application/offer/payment/enrollment suites passed. The legacy suite retained its behavioral assertions, with only its footer-version expectation updated. It caught an action-name collision with old family messages; new dispatch now uses an explicit action allowlist, preserving those routes.

A separate 5.3.35 installation used its existing updater. Checks passed for injected-failure recovery, installation with matching hashes and unchanged configuration, same-version refusal, explicit prior-file/version rollback and traversal rejection.

The cumulative archive has 36 approved application files plus release.json. Each member matched the manifest and current-source SHA-256 before upload. Configuration, keys, provider credentials, fixtures, helpers and test certificates are excluded. Preparation is additive; file rollback is not a database rollback.

These are local checks, not deployment to or certification of the user's hosted database, SMTP account, DNS authentication or inbox delivery. Remote dedicated-demo refresh was not performed; its schema boundary and external-action restrictions were checked locally. No real payment, parent email or WhatsApp message was sent. Staff identity/relationship verification remains essential.
