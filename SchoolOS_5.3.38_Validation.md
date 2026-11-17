# SchoolOS 5.3.38 — Validation

Local PHP 8.4, MariaDB and Chromium/Playwright checks using fictional school data.

| Checks | Passed | Failed |
|---|---:|---:|
| Staff provisioning and operational readiness scenarios | 38 | 0 |
| Authorization, tenant scope, family-link and demo boundaries | 6 | 0 |
| Staff invitation → request → approval → first-password flow | 4 | 0 |
| Final directories, searchable recovery and connection correction | 3 | 0 |
| Current-session assessment readiness | 1 | 0 |
| Browser scenarios | 6 | 0 |
| Final responsive layouts (360px/1440px, light/dark) | 20 | 0 |
| Fourteen-role read-only route smoke checks | 735 | 0 |
| Existing 5.3.37 updater install/recovery/rollback checks | 5 | 0 |
| PHP syntax checks | 42 | 0 |

Modified JavaScript also passed node --check.

The 38 provisioning scenarios include all 29 job profiles, exact granted capability sets, connected HR/staff/teacher records, mandatory initial password change metadata, preserving existing HR salary, atomic rollback on invalid record selection, repeated-connection idempotency, retaining existing permissions and attendance eligibility.

Browser checks actually signed each of the 29 newly created profile accounts in with its school sign-in ID, changed its temporary password and opened its assigned workspace. They also checked school-admin navigation for fatal errors and placeholder text, account-specific parent/child links, teacher allocations, dashboard form choices, conditional teacher fields, direct HTTP creation/handover and invalid-CSRF refusal. The final layout pass covered the updated overview, expanded staff form, account connections, access setup and guardian directory in both themes and viewport sizes.

The invitation tests temporarily enabled the local global member-registration switch, then restored its original value. Requests stayed inactive until reviewed; approval connected records and capabilities, and the issued credential required a personal password. No real email, SMS or WhatsApp was sent.

Boundary checks cover foreign-school accounts and HR records, insufficient identity verification, invalid CSRF, forbidden account types, incomplete family linking, existing-account type preservation and refusal of staff permission/invitation changes in shared demo mode. Demo boundaries were exercised through the actual demo guard constant; an isolated public demo deployment was not provisioned for these tests.

The unchanged 5.3.37 updater passed injected-failure recovery, complete installation with matching source hashes and untouched configuration, same-version refusal, explicit file/version rollback and ZIP traversal rejection.

The final package contains 36 approved source files plus release.json, compared against its manifest and current source. Configuration, keys, private credentials, fixtures and test files are excluded. Synthetic fixture tenants are cleaned after verification.

These are local implementation checks. They do not certify all features of the full application for production, validate historical school data, prove external provider delivery/capacity or confirm that the hosted site has installed the update.
