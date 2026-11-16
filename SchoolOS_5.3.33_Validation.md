# School OS 5.3.33 — Validation

Local validation on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright with fictional role accounts. The user's PC runtime and Windows settings were not accessible; its exact cause remains unconfirmed.

| Check group | Passed | Failed |
|---|---:|---:|
| Dashboard/theme/mobile checks across 14 roles | 88 | 0 |
| Desktop startup, preferences and recovery cases | 9 | 0 |
| Update installation and rollback | 5 | 0 |
| Packaged PHP and changed JavaScript syntax | 25 | 0 |

## Recovery cases

1. Emulated desktop reduced motion reproduces the stationary scene. A visible Play control and an explanatory title identify the preference-related pause.
2. Clicking Play starts movement and colour cycling despite that desktop preference. The explicit background choice survives reload. Other reduced-motion UI behavior is not globally enabled.
3. Pause stops movement/colour cycling and survives reload for the account/browser.
4. A deliberately non-calling `requestAnimationFrame` is recovered by the timer driver. Movement resumes through the fallback. The test uses timer polling so its own assertion does not depend on the deliberately stalled frame API.
5. An injected error after the animation bootstrap cannot prevent background movement. This tests separation from later dashboard helper code.
6. A stored desktop pause choice does not stop the mobile animation. The new control is hidden and the mobile animation profile remains selected.
7. An explicitly enabled reduced-motion desktop background still pauses its positions and colour animation when a hidden-tab event is simulated.
8. A simulated background geometry/startup error is contained, displays Background unavailable and leaves the dashboard navigation rendered.
9. Native desktop hover and the Applications navigation remain connected.

The recording reproduces the reduced-motion scenario, enables the background through Play, pauses it and resumes it. Its final state was running and actual collisions occurred during capture. This is a recording of the implementation, not a separate animation mockup.

## Role and layout checks

Platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer homes were checked in both themes at 1440px and 360px widths. Checks cover the shared shell, personal welcome, page-width overflow, mobile menus, theme switching/persistence and absence of captured page errors/PHP runtime warning signatures. Nine specialist working pages were also checked in both themes at phone width.

These local checks do not certify all Windows/browser/GPU combinations, physical iOS/Android behavior or a comprehensive accessibility standard. No real financial transactions, external messages, hosted installation or separate hosted-demo environment were exercised.

## Installer and integrity

The existing **5.3.32 updater** was tested on an isolated prior-version application copy. Five checks passed: recovery after an injected mid-install failure, complete installation matching every manifest hash while preserving configuration, same-version refusal, explicit rollback to original files/metadata, and traversal-entry rejection before file changes.

The ZIP contains exactly 34 approved application files plus `release.json`. Every member was compared with the source and its manifest SHA-256. Changes are limited to `portal_experience.php`, `portal_experience.css`, `portal_experience.js` and `VERSION.txt`. The new setting is local to browser storage; school database schemas, business handlers and authorization rules are unchanged. Configuration, credentials, test scripts and fixture records are excluded.

The MP4/JPEG previews are outside the application archive. See the versioned checksum file for the exact ZIP hash.
