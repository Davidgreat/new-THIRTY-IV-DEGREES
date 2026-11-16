# School OS 5.3.29 — Glass dashboards

[Download the admin-installable update](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.29_Glass_Dashboards_Update.zip)

[Light-mode preview](SchoolOS_5.3.29_light_preview.jpg) · [Dark-mode preview](SchoolOS_5.3.29_dark_preview.jpg)

The dashboard finish now follows the supplied visual references: translucent frosted panels, reflective edges, layered shadows, soft 3D spheres and a bright cyan/violet/peach palette. Colour passes through the panels while forms, data and chart labels retain readable contrast. These are working portal screenshots with fictional demo records, not static dashboard mockups.

## Install

1. Back up application files and database.
2. Download the ZIP from GitHub using **Download raw file**.
3. Install it through **Platform Admin → Core updates**, then refresh the portal.
4. Open the existing account and try both themes using the header’s theme button. If an old browser tab retains cached styles, reload it.

This is a cumulative update containing 34 approved application files and `release.json`, including the preceding admissions update. Existing real/demo accounts use the finish through the shared dashboard shell; no account recreation or per-school activation is needed. It adds no database tables, configuration, credentials, paid services or external image/font downloads. Individual module feature-version labels may remain at their preceding release; the installed core version is 5.3.29.

## What changes

- **The dashboard shell:** A frosted sidebar and header, restrained cyan/violet active-navigation treatment and a shared decorative background. The three shaded colour forms sit behind the working page and remain stationary.
- **Working panels:** Frosted cards with brighter top edges, translucent fills, rounded corners and layered inner/outer shadows. The shared treatment covers the general overview and existing HR, driver, parent, student, teacher, library, school-store, communications and admissions components.
- **Overview and report cards:** Existing charts retain their original values, segments and meanings. Doughnut centres use a readable solid surface with subtle depth rather than letting ring colours show through their numbers. Metric and action cards receive the same visual finish.
- **Light and dark modes:** Pale, luminous glass in light mode and deeper navy glass in dark mode. Dark-mode forms, menus, table headers, secondary labels and errors have explicit surfaces/colours. The existing theme switch and preference persistence remain in use.
- **Phones:** Smaller blur radius, restrained decoration, readable controls and 16px text-entry fields to avoid automatic text-field zoom on supporting mobile browsers. Mobile navigation and form layouts continue to use the existing responsive behavior.
- **Accessibility and printing:** Background shapes are hidden from assistive technologies and cannot intercept clicks. Hover lifting is restricted to fine-pointer devices without a reduced-motion preference. Reduced-transparency users get opaque panels; forced-colour mode removes decoration/filter effects. Printing removes the scene and uses dark text on white panels.

The background is made with local CSS gradients; no supplied stock-image watermark/artwork is copied into the application. There is no animation loop, mouse-following tilt or new JavaScript processing for the decorative scene. Blur is lighter on smaller screens, although actual performance still depends on the device/browser. Browsers without backdrop-filter support receive an opaque fallback.

## Scope

The active change from 5.3.28 affects four files: `index.php` (dashboard decoration/scope), `portal_experience.php` (stylesheet cache version), `portal_experience.css` and `VERSION.txt`. Admissions, finance, permissions, account linking and other workflow logic are unchanged. The ZIP includes previous cumulative files so earlier fixes are retained.

This release styles authenticated dashboard pages. It does not redesign the public website, login screen, standalone printable documents or standalone live-class player. The teaching dashboard and embedded lesson cards receive the shared treatment.

[Validation details](SchoolOS_5.3.29_Validation.md) · [SHA-256 checksum](SchoolOS_5.3.29_SHA256SUMS.txt)

Tested locally with demo accounts. This session did not install the update on the hosted school.
