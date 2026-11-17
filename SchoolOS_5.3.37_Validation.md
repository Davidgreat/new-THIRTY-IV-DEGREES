# School OS 5.3.37 — Validation

Local verification with PHP 8.4, MariaDB and Chromium/Playwright using fictional school accounts.

| Checks | Passed | Failed |
|---|---:|---:|
| Live-account browser scenarios | 6 | 0 |
| Shared-demo layout and anonymous preview scenarios | 2 | 0 |
| Role, preparation and demo rendering checks | 4 | 0 |
| Existing-updater install/recovery/rollback | 5 | 0 |
| PHP syntax | 42 | 0 |

Changed JavaScript also passed node --check.

The live-account scenarios cover a visible link card on both school admin and admissions homes; correct clipboard URL and parent-form preview; generation from admin home; no generation controls for admissions; paused-state handling and admin re-enabling; clear missing-origin guidance; and visible controls with no phone overflow in both themes.

Shared-demo layout scenarios render the actual demo branch for both roles and check populated example links, visible preview/copy buttons and separated panel rectangles at 1366px/360px in both themes. Expanded settings were also inspected. The anonymous preview opens its example form, adds another child and refuses POST with HTTP 405. Its submit action is disabled, and no registrations or personal data are saved.

Role checks verify that parents, students, teachers, ordinary staff and platform accounts do not receive school link-management cards. Missing-schema states show preparation only to school admin and a clear administrator handover instruction to admissions. Shared demo controls are clearly distinct from live school registration links.

The unchanged 5.3.36 updater passed injected-failure recovery, full 5.3.37 installation matching the manifest with configuration preserved, same-version refusal, explicit prior-file/version rollback and traversal rejection.

The final ZIP contains 36 approved files plus release.json, each compared against its manifest and current source. Local configuration, keys, credentials, synthetic data, test scripts and temporary rendered demo pages are excluded.

This patch adds no tables and does not alter enrollment/account approval/email-delivery handlers. It changes dashboard discovery, demo preview, layout, asset versions and one-time preparation's return destination. The live school's installed version, settings and database were not inspected or changed; these are local checks, not a hosted deployment claim.
