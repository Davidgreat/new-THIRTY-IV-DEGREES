# School OS 5.3.34 — Validation

Local validation on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright with fictional account records.

| Check group | Passed | Failed |
|---|---:|---:|
| Dashboard/theme/mobile checks across 14 roles | 88 | 0 |
| Automatic playback and recovery checks | 6 | 0 |
| Update installation and rollback | 5 | 0 |
| Packaged PHP and changed JavaScript syntax | 25 | 0 |

## Autoplay checks

1. A desktop context with reduced motion enabled starts background movement and colour cycling automatically. No background Play/Pause control exists in the DOM. Reload starts it again without a click.
2. A saved old background preference of off does not stop desktop autoplay.
3. A deliberately stalled requestAnimationFrame recovers automatically through the timer driver, including in the reduced-motion desktop context.
4. Hidden-tab events pause positions and colour cycling; returning resumes playback automatically.
5. Mobile retains its normal moving profile and has no playback control. Mobile's own reduced-motion preference still freezes the background.
6. Reduced-transparency and print emulation still hide the decorative scene and pause its simulation.

## Role regression

Platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer homes were checked in light/dark mode at desktop and phone widths. Checks cover the shared dashboard shell, personal welcome, overflow, mobile menus, theme switching/persistence and absence of captured browser/PHP errors. Nine specialist working pages were checked in both themes at phone width.

These are local browser checks, not direct inspection of the hosted school or certification of every physical PC/mobile/GPU combination. No live payments, external messages or production database changes were performed.

## Installer and package

An isolated preceding-version copy used the unchanged 5.3.33 updater. All five checks passed: recovery after an injected mid-install failure, complete installation matching the manifest while retaining configuration, same-version refusal, explicit rollback to prior files/version and traversal-entry rejection before file changes.

The package contains exactly 34 approved files plus release.json. Each archive member was compared with its source and manifest SHA-256. Changes are confined to portal_experience.php, portal_experience.css, portal_experience.js and VERSION.txt. The setting/button code has been removed; older local background pause values are ignored rather than used to gate startup. Business handlers, database schemas and permission rules are unchanged. Configuration, credentials and test scripts/fixtures are excluded.

See the versioned checksum file for the exact archive hash.
