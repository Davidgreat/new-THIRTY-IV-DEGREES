# School OS 5.3.30 — Validation

Local checks on 16 November 2026 using PHP 8.4, MariaDB and Chromium/Playwright. Screenshots contain fictional account records.

| Check group | Passed | Failed |
|---|---:|---:|
| Dashboard, welcome, theme and mobile checks across 14 roles | 88 | 0 |
| Page regression across 14 roles | 695 | 0 |
| Ambient motion, hover/touch, preferences and tab pause checks | 6 | 0 |
| Admissions welcome, presentation and shortcut checks | 5 | 0 |
| Update installation and rollback | 5 | 0 |
| Packaged PHP and changed JavaScript syntax | 25 | 0 |

## Dashboard and welcome coverage

Platform admin, school admin, teacher, parent, student, admissions, partner, HR, driver, warden, librarian, school store, communications and reviewer homes were checked in light/dark modes at 1440px and 360px widths. The shared personal welcome is present exactly once, visible, and contains the account’s own name. Checks also cover the shared glass background, running ambient animation, no page-width horizontal overflow, mobile menu opening/closing and persisted theme switching. No captured browser page errors or PHP warning/error signatures occurred.

Working pages for nine specialist roles were checked in both themes at phone width: HR, teaching/live lessons, Finance, parent reports, school-store items, library catalogue, transport, applications and communications. Controls remain available and the shared dashboard shell is present. The role link crawl opened 695 pages without HTTP failures or PHP runtime warning/error signatures. This is a route regression, not a claim to retest every financial or school workflow.

The final admissions-specific checks verify one visible personal welcome, no extra generic home introduction, exactly one Add an application shortcut, and no horizontal overflow in both themes at desktop/phone widths. The Applications workspace still displays its contextual header and opens the connected application form through the shortcut.

## Motion and interaction checks

- Background transforms change over time; the float cycles are slow and the faded opacity is at most 25% in both themes. The colour-blend animation is present.
- Hovering a navigation item starts its breathing shadow/glow and clicking it still opens the destination.
- A touch-only browser context does not start the hover animation and fits within the phone viewport.
- A simulated visibility change pauses and resumes the decorative animation. This tests the visibility handler; it is not a battery benchmark.
- Emulated reduced motion stops floating, colour blending and hover animation while retaining a visible keyboard focus indicator.
- Emulated reduced transparency hides the scene and stops its animation. Print emulation from dark mode hides decoration and retains readable text/surfaces.

Representative desktop/mobile screenshots were visually checked for softened colours and the restored personal greeting. The preview files are static captures; they cannot demonstrate the animation itself. Physical iOS/Android devices, low-end GPU performance and a comprehensive WCAG audit were not covered.

## Dedicated sandbox limitation

The fictional role accounts used above are available through the ordinary local test database. A separate sign-in using the isolated-demo option was also attempted, but that local sandbox sign-in reported that the demo was unavailable/details incorrect. That separate environment was therefore not validated. This is not evidence about the hosted school's sandbox. The welcome change is implemented in the same shared home renderer for ordinary and demo sessions and requires no account-specific migration.

## Installer and package

The preceding **5.3.29 updater** was exercised against an isolated prior-version application copy. All five checks passed: injected mid-update recovery, complete manifest-matching installation with unchanged configuration, same-version refusal, explicit rollback to original files/version, and traversal-entry rejection before file changes.

The ZIP has exactly 34 approved files plus `release.json`. Every packaged file was compared with its manifest SHA-256 and source. Relative to 5.3.29, changes are limited to `experience_ui.php`, `experience_admin.php`, `portal_experience.php`, `portal_experience.css`, `portal_experience.js` and `VERSION.txt`. The admission-renderer change controls presentation of the home introduction; action handlers are unchanged. Credentials, configuration, fixtures and test/debug scripts are excluded.

See the versioned checksum file for the exact archive hash. No hosted installation or real external messages/payments were performed during this validation.
