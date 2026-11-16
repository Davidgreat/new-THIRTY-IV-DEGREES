# School OS 5.3.32 — Validation

Local checks on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright. All account records in the test environment and previews are fictional.

| Check group | Passed | Failed |
|---|---:|---:|
| Dashboard/theme/mobile checks across 14 roles | 88 | 0 |
| Desktop travel, native hover, assets and mobile comparison | 7 | 0 |
| Update installation and rollback | 5 | 0 |
| Packaged PHP and changed JavaScript syntax | 25 | 0 |

## Focused desktop checks

At 1366px by 768px, the first circle is at least 500px across. Sampled movement spans more than 220px over several seconds, and real collisions are observed. This checks travel across the background rather than just the presence of an animation declaration.

The Applications tab receives its coloured background, 1.07 scale transform and outward-breathing animation. Multiple samples confirm that the outline expands over its cycle, and clicking still opens Applications. The same hover appearance and click were checked in a browser context with dashboard JavaScript disabled, proving that this specific effect is provided directly by CSS.

The new asset endpoints return the exact stylesheet/JavaScript bytes with the correct content types, `no-store` cache instructions and no session cookie. Unknown names, traversal-like names and array inputs return 404. The route uses a fixed two-file whitelist and exits before normal session/database startup.

Mobile rendering was compared with the actual preceding 5.3.31 CSS/JavaScript loaded into a matching phone viewport. Circle dimensions, static positions, transparency, blur treatment and computed colour-animation configuration match. Source review also confirms that the mobile size/speed/seed expressions retain the preceding behavior, and new colour/hover overrides are inside the desktop-width media query.

Reduced-motion emulation freezes desktop movement and disables hover enlargement. No browser runtime errors were captured in the focused journey.

## Shared role coverage

The broader browser checks cover platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer. Homes were opened in both themes at 1440px and 360px widths, checking the glass shell, personal welcome, animation presence, page-width overflow, mobile menus, persisted theme switching and absence of captured browser/PHP errors. Nine specialist working pages were also checked in both themes at phone width.

The desktop recording observed four collision events during capture. Representative frames were inspected for larger circles and the Applications hover highlight. These are local Chromium checks, not a physical Windows/iOS/Android compatibility certification or a complete WCAG audit.

Read-only attempts to retrieve the hosted public assets were blocked by the execution environment's network proxy. The hosted browser's cached assets and runtime therefore could not be inspected directly. No hosted installation or separate isolated-demo-database test was performed in this session.

## Package and recovery

An isolated preceding-version copy used the unchanged **5.3.31 updater**. All five checks passed: recovery after an injected mid-update failure, complete manifest-matching installation with unchanged configuration, refusal to reinstall the same version, explicit rollback to original files/version, and traversal-entry rejection before file changes.

The ZIP contains exactly 34 approved application files plus `release.json`. Every packaged file was compared with its source and manifest SHA-256. Configuration, credentials, test/debug scripts and fixture records are excluded. Relative to 5.3.31, only `index.php`, `portal_experience.php`, `portal_experience.css`, `portal_experience.js` and `VERSION.txt` change. Business transaction handlers and permissions are unchanged.

The preview files are outside the application ZIP. See the versioned checksum file for the exact archive hash.
