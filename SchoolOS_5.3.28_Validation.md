# School OS 5.3.28 — Local validation

Date: 16 November 2026. Environment: local PHP 8.4, MariaDB and Chromium/Playwright. Fixtures were fictional and isolated under a synthetic school; they were removed after the checks. No hosted-school installation, real financial transaction or external message was performed.

| Check group | Passed | Failed |
|---|---:|---:|
| Server workflow/access/data assertions | 20 | 0 |
| Browser journeys and mobile checks | 11 | 0 |
| Role page regression across 14 accounts | 695 | 0 |
| Update installation and rollback | 5 | 0 |
| Packaged PHP syntax and changed JavaScript syntax | 25 | 0 |

## Server workflow checks

1. Fresh active admissions/admin identities, school scope and CSRF enforcement.
2. Separate pupil/guardian data, real class, fee snapshot and private family link.
3. Repeat-submission handling, active-application duplicate guard and foreign-class rejection.
4. Pre-offer corrections, preserved fee history, duplicate identity rejection and revoked old family access after guardian email change.
5. No acceptance/enrollment bypass; pending/rejected documents prevent offers.
6. Checked replacement documents can supersede an older matching file without deleting history.
7. Offer/class/acceptance fee snapshot and no repeated acceptance charge.
8. Expired offer refusal and no assessment/interview rewind of accepted applications.
9. Unpaid charge enrollment guard, admin-only payment confirmation and repeated confirmation handling.
10. Wrong guardian login, unavailable student login and wrong class are refused without creating a pupil.
11. Conflicting existing guardian identity rolls back the complete enrollment transaction.
12. Successful pupil, Student Records, guardian, approved account and current-class handover.
13. Repeated enrollment/verified account linking creates no duplicate pupil or account links.
14. Enquiry conversion records the child separately and cannot convert the same enquiry twice.
15. Replaced tracking access, internal note separation and in-platform family update storage.
16. Fixed entrance question set, stable invitation and closure after an offer.
17. Legacy accepted record without an offer requires administrator review and renewed acceptance.
18. Admission-related parent chat in both directions, with unrelated-parent/student restrictions.
19. Due reminder notification scope and completion.
20. All seven desk sections/six applicant tabs render; account search is bounded and the Finance admission log renders.

## Browser checks

- Existing admissions role opens the new seven-section overview with six actionable totals, stage doughnut and no generic My Tasks link.
- Anonymous family submission, private receipt/tracking page and invalid-key refusal.
- Family-to-office messages and office replies; internal notes excluded from the family page.
- Actual PDF upload, checked document review, authorized download and refusal through a parent's staff-document request.
- Administrator adds an entrance question, admissions issues a private invitation, preparation precedes Start, applicant submits once.
- School-branded printable offer, guardian acceptance and refusal to enroll before charges are confirmed.
- Administrator records the two external-payment confirmations; admissions enrolls and the resulting pupil appears in both parent and student dashboards.
- Registered guardian/admissions school chat, reply visibility and private-link replacement revocation.
- Enquiry conversion with separate pupil identity and linked application.
- Application correction, replacement family page and phone-width correction form.
- Every main section and applicant tab fits a 360px viewport without page-level horizontal overflow. Family tracking fits too. Admissions APIs reject wrong CSRF and parent access.

Screenshots were visually inspected for desktop, light mobile and dark mobile layouts. Browser checks exercised one Chromium installation; physical iOS/Android devices and assistive technologies were not comprehensively tested.

## Role regression and packaging

The local link crawl opened 695 pages across platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer accounts, without HTTP errors or PHP runtime-warning signatures. This is a route regression, not proof of every mutation or a production load test.

The unmodified preceding **5.3.27 updater** was tested against an isolated prior-version application copy:

1. Injected mid-update failure restored all prior file hashes.
2. Complete installation matched every new manifest hash and committed its transaction journal; configuration stayed unchanged.
3. Reinstalling the same version was refused.
4. Explicit rollback restored all original files and prior version metadata.
5. A traversal ZIP entry was rejected before file changes.

The cumulative package contains exactly 34 approved application files plus `release.json`. Each manifest SHA-256 was compared with the packaged source. Configuration, credentials, fixture records and audit/debug scripts are excluded. See the checksum file for the exact archive hash.

Operational scope and remaining boundaries are documented in the [audit](SchoolOS_5.3.28_Admissions_Audit.md). Passing local checks does not independently certify the live hosting configuration.
