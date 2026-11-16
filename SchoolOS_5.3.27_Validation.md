# School OS 5.3.27 validation

Local PHP/MySQL and Chromium with isolated fictional school records. No real external messages, provider charges or live-school data changes occurred.

## Fifteen workflow/access checks passed

Dedicated role home and management denial for other roles; bidirectional parent/communications chat boundaries; draft idempotency and revision checks; shared publication with per-recipient deliveries and repeated-publish safety; recipient read confirmation; future scheduling and stopping; class-scoped event visibility; poll publication/audience/choice/closing/duplicate checks; saved-message ownership; contact-change protection and consent separation; suppressed external delivery without provider I/O or credits; private personalised posts; revoked access; published event/poll cancellation/closure; all eight populated desk views.

## Three large-school checks passed

A separate fictional school with 131 active accounts was used. The first in-app batch delivered 100 records and the next delivered the remaining 31, using one shared Hub post. A personalised broadcast then confirmed that early and late recipients both retained their own alert beyond the former sixty-post boundary without exposing another person's name. No messaging credit movements occurred.

## Nine browser checks passed

1. Communications login, dedicated home, six totals, pie and eight sections; generic My Tasks absent.
2. Parent-only draft → publication → parent Hub → explicit read confirmation → delivery report; student cannot see it.
3. Class name search → event publication → parent calendar and student announcements.
4. Parent poll response returns to the selected-child context and appears in the report.
5. Parent and communicator exchange real in-platform chat messages on separate browser sessions.
6. Parent submits contact; communicator finds and verifies it without changing consent.
7. Saved-message action opens compose with its connected title/body.
8. Published event cancellation and poll closure reach the parent and retain responses.
9. All eight pages fit 360px; light/dark screenshots inspected; live summary works; invalid tokens and parent staff-search requests are refused.

## Role regression and installer

Read-only authenticated regression visited 678 pages across 14 roles with no HTTP/page failures, PHP warnings, fatal/parse errors or undefined-function/method errors. Changed PHP and JavaScript syntax checks passed.

All five existing-updater checks passed: injected mid-install failure recovery, complete 34-file installation with matching manifest/configuration/journal, duplicate-version refusal, explicit rollback to 5.3.26 and traversal rejection. The final package's hashes were compared with the validated source.

The existing external provider integration was preserved. Consent suppression was tested without provider calls; real email/SMS/WhatsApp/push delivery and hosted cron configuration were not tested. The desk's automatic processor sends only in-app records. Read confirmation means an explicit user action, not a verified claim that the person understood the notice.

Synthetic fixtures were cleaned after testing. No credentials, local configuration, database content or test scripts are shipped in the cumulative ZIP.
