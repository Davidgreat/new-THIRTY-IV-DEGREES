# School OS 5.3.31 — Validation

Local checks on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright. Account records used in tests/previews are fictional. The hosted school and its separate isolated-demo database were not exercised in this session.

| Check group | Passed | Failed |
|---|---:|---:|
| Dashboard/theme/mobile checks across 14 roles | 88 | 0 |
| Motion, collision and interaction checks | 9 | 0 |
| Keyboard, disabled controls and display preferences | 5 | 0 |
| Update installation and rollback | 5 | 0 |
| Packaged PHP and changed JavaScript syntax | 25 | 0 |

## Role and layout coverage

Platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer homes were opened in both themes at 1440px and 360px widths. Checks cover the shared glass shell, personal welcome, ambient colour animation, no page-width overflow, mobile menu opening/closing, theme switching/persistence, and absence of captured browser page errors or PHP runtime-warning/error signatures.

Nine specialist working pages were also checked in both themes at phone width: HR overview, live teaching dashboard, Finance, parent reports, store items, library catalogue, driver journeys, applications and communications. The controls remain present and the shared shell is applied.

## Motion and click behavior

The targeted browser journey verified:

1. Bubbles have no blur filter, retain at most 25% opacity, and visibly change position by more than 18px within approximately one second on the desktop test viewport.
2. Actual simulation collisions occur; the contacted pair separates afterward rather than remaining overlapped. This observes the running implementation, not a manually triggered collision animation.
3. Colour-blend opacity changes substantially during a short interval.
4. The application action receives a strong ring/glow and its normal click still opens the application form. Hover pulse does not continuously resize the clickable target.
5. An ordinary help link receives text glow and a stronger underline.
6. A newly inserted link receives feedback through delegation without a reload.
7. Reduced motion stops movement and colour animation while preserving separate static bubble positions.
8. A simulated hidden-tab event pauses/resumes movement without a large time jump. This checks the visibility handler, not battery use.
9. A touch-only mobile context has visible bubbles without sticky hover feedback or page-width overflow.

Five further checks verify keyboard focus, exclusion of disabled buttons, and stopping/hiding the decorative simulation under reduced transparency, forced colours and print emulation. The recording session also observed real collision events while capturing the motion preview.

Representative screenshots and a frame from the recorded video were visually inspected for crisp background circles, the preserved transparency and readable dashboard content. Physical iOS/Android devices, low-end hardware performance and a comprehensive WCAG audit were not covered. The decorative movement is not a production load benchmark.

## Package and rollback

An isolated prior-version application copy used the unchanged **5.3.30 updater**. The following checks passed:

- Injected failure partway through installation restored every prior file hash.
- Complete installation matched the new manifest hashes, preserved configuration and committed the journal.
- Installing the same version again was refused.
- Explicit rollback restored original files and 5.3.30 metadata.
- A traversal entry was rejected before file changes.

The archive contains exactly 34 approved files plus `release.json`. Every archive member was compared with its source and manifest SHA-256. Changes from 5.3.30 are confined to `portal_experience.php`, `portal_experience.css`, `portal_experience.js` and `VERSION.txt`. Backend handlers, admissions processing and permissions are unchanged. Configuration, test scripts, fixture records and credentials are excluded.

The preview MP4/JPEG files are documentation outside the application ZIP. See the versioned checksum file for the exact archive hash. No hosted installation or real external messages/payments were performed during these checks.
