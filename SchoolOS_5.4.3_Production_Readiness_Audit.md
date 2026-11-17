# SchoolOS Nigeria — production-readiness audit

**Release reviewed:** 5.4.2, with verified fixes and current guides delivered in 5.4.3.  
**Audit date:** 17 November 2026 (WAT).  
**Recommendation:** prepare a supervised pilot after installing 5.4.3 and completing the essential live-host checks below. Do not describe this audit as unconditional approval for an unrestricted public production launch.

The exercised application workflows have a solid tested baseline. Four reproducible compatibility/usability defects were fixed, role and tenant boundaries were exercised, and the out-of-date manual was replaced. No critical security failure was found in the scenarios exercised. This is a bounded code/workflow audit, not an independent penetration-test, legal/accounting certification, production load test or guarantee that every record/host/provider combination is safe.

## 1. What was actually examined

The current local PHP source and cumulative update, public routing, authentication/session recovery, modular access, tenant/child scope, finance, admission/family onboarding, learning/reports, HR, transport, boarding-related controls, library, school store, communications, classroom control contracts, workers, updater and public guides were examined through source review and relevant regressions. Local execution used PHP 8.4.24, MariaDB 11.8.6 and Chromium 156. Code syntax requires PHP 8.1 or later; a maintained production runtime is required.

Tests ran in a newly created ownership-marked database containing only fictional records, separate from the existing local database. The main local sandbox configuration was not repointed. No hosted database, real bank transfer, live school email/WhatsApp send, real classroom-provider account or real pupil data was used. The synthetic database and temporary private audit files are removed after evidence capture.

Read-only checks of `https://getschoolos.com.ng/`, login/documentation and known deployment paths all returned the same generic HTTP 403 from this environment. Chromium could not establish a trusted TLS session from its environment. These results do not establish that ordinary visitors are blocked, that the live certificate is invalid, or that each private-path rule works. They mean independent live-host verification remains required. The audit did not bypass those responses or change the live site.

## 2. Confirmed defects fixed in 5.4.3

| Priority | Finding | Impact and evidence | Fix and verification |
|---|---|---|---|
| Medium | Parent academic-homework query compared differently collated session fields | A clean mixed-collation installation raised SQL error 1267 when parents opened homework. | Normalised the specific comparison to supported UTF-8 collation, without changing stored data. All 19 parent/report regressions pass. |
| Medium | Class-announcement teacher eligibility used a mixed-collation comparison | Class-targeted communications processing failed when checking a teacher allocation, also preventing subsequent due messages. | Normalised the allocation/session comparison. All 15 communications regressions pass, including audiences, scheduling, read acknowledgements, consent and cancellation. |
| Low | Personal employment context advertised an unassigned operations menu | Seven specialist roles encountered an operations link that then returned 403. This was a navigation error, not evidence of unauthorised data access. | Removed current-page context from the general workspace permission decision. Personal HR routes remain usable for staff/teachers/admissions; unauthorised general operations stay denied. Eight representative employee identities pass focused rechecks. |
| Low | Platform Reports was a visible placeholder | The platform operator could open a menu that did not provide an implemented report. | Replaced it with actual school/login/subscription-history summaries and verified platform-checkout totals, with clear financial limitations. Operator-only access and mobile rendering checked. |
| Documentation | Built-in guides still said release 5.3.0 | Important onboarding, permissions, leadership, family, store, classroom and operational changes were missing. | Replaced with 47 searchable guide entries, all 35 job profiles, a 200-section full manual, print/PDF/offline HTML and task/role search. All 47 HTML/PDF pairs pass; phone/desktop light/dark checked. |

Additional hardening: the shared community-audience predicate now explicitly rejects a foreign tenant before evaluating any role; existing caller-level tenant filtering remains. Malformed guide and dashboard-section query input is rejected without PHP type warnings or fatal errors. An operator-only launch-facts panel distinguishes detected technical facts from live checks still needed.

## 3. Validation results

| Area | Fresh evidence |
|---|---|
| Initial authenticated navigation | 1,284 GET requests across all 41 demo identities, bounded to 50 pages per identity. Eight findings: the placeholder and seven dead-menu paths above; no PHP warning/fatal in that sweep. |
| Affected-role navigation after fixes | 244 requests across the affected platform/specialist/admissions identities; zero HTTP/error/placeholder findings. |
| Focused current workflow/security checks | 284 passing checks; zero remaining failures in the current acceptance set. |
| Web/PDF role guides | All 47 guide pages and their PDF endpoints return valid current-release output. |
| Browser checks | Guide directory, owner/parent/Principal/full-manual pages at 360px/1440px in light/dark; role/task search, guide text search, phone operator pages, overflow and JavaScript errors. |
| Syntax | 44 PHP/JavaScript syntax checks pass. |
| Update and rollback | Existing 5.4.2 updater installs the 43-file 5.4.3 package with matching hashes and unchanged configuration. Injected interruption restores files, repeated version and traversal are refused, explicit file rollback restores 5.4.2 with modular records present. |

The focused set covers teacher work publication/submission/grading, timed CBT/server marking, family/child access, branded report completeness/printing, active-account/session recovery, library issue/return/stock, store stock/order/invoice transitions, communications audience/consent/schedules, HR/attendance, regular/today-only collector rules, admission/registration/family approval, modular role scopes/revocation/independence, review cycles and classroom permissions.

A two-connection concurrency check confirmed that simultaneous confirmation of the same synthetic receipt posts one payment and one excess-credit adjustment, with a balanced ledger. This is one targeted race test, not a general concurrency or scale certification.

Password recovery was tested through real HTTP: existing sessions are revoked on their next request; temporary recovery requires a personal password; the old temporary password cannot be reused after that change. Anonymous resource/worker requests and unsigned payment callbacks were refused. Classroom checks validate scope, 30-minute duration rules, expiry/archive restrictions, microphone grants and room epochs; they do not prove live media transport or provider capacity.

Some older regression expectations were updated because the product intentionally changed: legacy family-link shortcuts are now refused in favour of verified onboarding; private chat pairs are reused; typing expiry is ten seconds; and regular approved collectors replace a daily-only request assumption. Current-contract checks cover these behaviours. Historical passing JSON was not counted as a fresh run.

## 4. Essential gates before the first real school

These are unresolved live acceptance items, not new features the platform silently performs.

| Gate | Who verifies | Acceptance evidence |
|---|---|---|
| HTTPS, runtime and private files | Hosting/platform operator | Supported PHP/extensions; normal outside-browser TLS/login; secure session cookies; actual unauthenticated denial of storage, config, database/backup archives and test tools. Confirm Apache/LiteSpeed rules or equivalent Nginx configuration. Verify the protected logo-upload folder if logo uploads are used. |
| Recoverable backups | Hosting/platform operator | Restore the matching database, application, uploads and private encryption keys to a separate environment. Record result, recovery owner and backup schedule. A file-update rollback is not this restore drill. |
| Real school identity and access | School Admin with responsible school staff | Correct school/class/session, one verified learner identity per pupil login, authorised guardian links, current teaching assignments, active employee/duty records and tested cross-family/cross-school denial. Test only the jobs/services the school activates. |
| Support, privacy and operating responsibility | Platform and school owners | Named support/incident owners, restricted privileged credentials, accurate privacy/retention/consent/collector policies, leaver access review and a launch support/rollback window. Have qualified advisers review applicable Nigerian obligations. |

Do not skip these gates because a dashboard reports that files/tables or startup records exist. The new **Platform Super Admin → Updates & Plugins → Before your first live school** panel shows useful facts, but explicitly leaves restore/provider/capacity checks as requiring live verification.

## 5. Additional gates only for services you plan to offer

- **Family email:** test actual inbox arrival, invalid recipient and retry/reissue. SMTP accepted is not proof of inbox arrival. New family accounts receive private one-time password-setup links valid for 72 hours; existing connected users retain passwords. Manual verified handover is an alternative where appropriate.
- **School/provider payments:** test exact reference/amount/NGN verification, idempotent retry, receipt, pupil credit, independent reconciliation and refund settlement with the actual configured provider. School fees and platform subscriptions use distinct records. Manual recording does not initiate bank movement.
- **Built-in live classroom:** use real teacher/learner devices on different networks, camera/microphone/screen permissions, waiting-to-start connection, rejoin/end and the intended class size. SFU has no fixed eight-person application cap, but service quotas, server resources and bandwidth constrain capacity. The direct fallback remains limited to eight people total. No unlimited free capacity is certified.
- **External communications, AI and push:** verify actual provider credentials, consent/templates/limits/credits and failure logging. Leave unused providers off. A saved connection or mock test is not production delivery.
- **Scheduled work:** configure and monitor the applicable CLI workers. HR closing processes calendar days and preserves recorded leave/exceptions; verify that policy and the midnight worker schedule. Family handovers, service deliveries and scheduled reports need appropriate processing. Page-triggered catch-up alone is not a promise of exact midnight/background execution.
- **Transport/boarding/library/store/payroll:** run a realistic school-specific example through staff and family views, including approvals and exceptions. Software records do not replace physical identity/safety checks, stock counting or accountant review.

A school does not need to activate every provider, role or service to launch core record management. Keeping an unverified optional service disabled is a valid rollout choice.

## 6. Launch recommendation and limits

Install 5.4.3 in staging, complete essential live gates, then start a small supervised cohort using verified services. Observe errors, failed handovers, pending reconciliation, account exceptions, database/storage use and provider quotas. Expand after a successful school operating cycle and a representative workload/capacity test.

Do not promise unlimited scale, guaranteed mail/media, an audited accounting statement, automatic legal compliance, arbitrary executable plugins or an independent security certificate. MFA is not implemented in this edition; review strong distinct privileged credentials and host/access-layer protections, and prioritise additional privileged-account protection as the service grows. A broader independent security and load assessment is appropriate before unrestricted multi-school expansion.

The code/workflow evidence supports a controlled pilot after the update and live sign-off. This audit cannot honestly certify the currently hosted service as unconditionally production-ready from the available access.

## 7. Install and find the new references

1. Back up and upload `SchoolOS_5.4.3_Launch_Audit_and_Current_Guides_Update.zip` unchanged through the real Platform Super Admin updater. This is a cumulative 43-file core update, not a plugin ZIP.
2. Confirm installed 5.4.3 and reopen Help / Guides. Start here appears before the complete manual; role filters and task search avoid an endless unfiltered catalogue.
3. Use the downloadable `SchoolOS_5.4.3_User_Manual.pdf`, `.html` or `.md` as an offline reference. The website offers individual role PDFs and offline HTML too.
4. Open platform Reports for the implemented summaries and Updates & Plugins for launch facts. Check parent homework/class announcements and specialist employment menus on staging.
5. Repeat the applicable live gates, record sign-off and begin the supervised rollout.

No production installation, production migration, live message or provider transaction was performed by this audit. The release does not reset school records, enable new providers or silently broaden existing roles.
