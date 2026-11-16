# Glass dashboards — validation

Local validation on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright. Account data used for screenshots is fictional demo data. No external services or financial mutations were exercised for this visual update.

| Group | Passed | Failed |
|---|---:|---:|
| Dashboard/theme/mobile/browser checks across 14 roles | 88 | 0 |
| Decoration/accessibility preference/printing checks | 5 | 0 |
| Existing-updater installation and rollback checks | 5 | 0 |
| Packaged PHP syntax checks | 24 | 0 |

## Account and layout coverage

The 14 tested roles were platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer.

Each role was opened in light/dark mode at 1440px and 360px viewport widths. Checks verified:

- The shared dashboard theme and decorative scene are present.
- Glass panels use backdrop blur and the legacy main background does not hide the scene.
- The document does not overflow horizontally.
- The new decorative scene has no running animations.
- Mobile navigation opens and closes through the menu button and backdrop.
- Theme switching changes the active theme and persists after reload.
- No captured JavaScript page errors or PHP runtime-warning/error signatures occur.

Nine additional role workspaces were opened in both themes at phone width: HR overview, live teaching dashboard, Finance, parent reports, store items, library catalogue, driver journeys, admissions applications and communications. Their controls remain present, the shared shell is applied, and the pages fit within the viewport without page-level horizontal overflow.

Screenshots were visually inspected for representative admissions, school administration and HR layouts, including dark mobile panels and chart labels. This is not a complete automated WCAG audit or a physical-device compatibility certification. Actual iOS/Android behavior and low-end GPU performance still depend on the browser/device.

## Preference and interaction checks

1. Decorative background shapes have `aria-hidden`, do not intercept pointer events, have no animation timeline, and do not block application navigation.
2. Emulated reduced motion removes the new transition; keyboard focus remains visible.
3. Emulated reduced transparency hides the scene and produces an opaque panel with no backdrop filter.
4. Emulated forced colours hides the decorative scene and removes panel filters.
5. Emulated printing from dark mode hides the scene and produces dark text on white panels.

The no-backdrop-filter fallback is supplied through CSS feature detection. Chromium supports backdrop filtering, so this run did not exercise a genuinely unsupported browser engine.

## Installation and source scope

The existing **5.3.28 updater** was tested with an isolated preceding-version application copy:

- Injecting a failure partway through deployment restored all prior file hashes.
- Successful installation matched every manifest hash, kept configuration unchanged and committed the update journal.
- Reinstalling the same version was refused.
- Explicit rollback restored the old files and 5.3.28 version metadata.
- A ZIP traversal entry was rejected before files changed.

The archive contains exactly 34 approved application files plus `release.json`. Its manifest hashes were compared with every packaged source file. Relative to the preceding release, only `index.php`, `portal_experience.php`, `portal_experience.css` and `VERSION.txt` change. The PHP differences add decorative dashboard markup and advance the stylesheet version; existing workflow handlers and permissions are unchanged. No new JavaScript is included.

The archive excludes configuration, login credentials, test scripts and fixture data. The two preview images are repository documentation and are not required by the application or installed from the ZIP. See the versioned checksum file for the exact archive hash.

The hosted school was not changed during this validation. Install through Core updates and continue the school's own account/device acceptance checks.
