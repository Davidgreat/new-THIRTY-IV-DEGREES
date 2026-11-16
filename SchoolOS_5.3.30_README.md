# School OS 5.3.30 — Living glass dashboards

[Download the admin-installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.30_Living_Glass_Dashboards_Update.zip)

[Light preview](SchoolOS_5.3.30_light_preview.jpg) · [Dark preview](SchoolOS_5.3.30_dark_preview.jpg)

This update adds subtle movement and responsive feedback to the shared glass dashboard finish, softens the background colours, and restores the personal welcome on specialist dashboard homes.

## What changes

- **Softer colour:** Background circles now use approximately 22–23% opacity, down from 58–68%, with softer edges and less intense shading. Small decorative forms within dashboard banners are faded too. Light and dark themes retain their own readable surfaces.
- **Slow ambient movement:** The circles gently float over 38–48 second cycles. A second gradient layer gradually fades between soft colour blends. Shapes move only a small distance and cannot intercept clicks. No mouse-following effect or JavaScript frame loop is added.
- **Menus that respond:** Fine-pointer hover adds a gentle lift, soft glow and breathing shadow to navigation, buttons and actionable cards across the authenticated dashboards. Selected states and status colours retain their meaning. Disabled controls do not glow. Touch devices use a small press response without persistent hover animation.
- **Personal welcome restored:** Every account’s home now renders the shared greeting before opening its specialist workspace. It includes the account name, role-specific introduction, school and the existing date treatment. Admissions, parent, driver, library, school-store and communications homes previously returned into specialist renderers before reaching this greeting.
- **A cleaner admissions home:** The personal greeting replaces the additional generic admissions introduction on the home dashboard. The Add an application shortcut stays available. The full Applications workspace still has its contextual heading and connected application form.
- **Motion preferences:** Reduced-motion users receive stationary backgrounds and no breathing/hover animation. The new ambient movement pauses while the browser reports that the tab is hidden. Reduced transparency and forced-colour preferences retain the preceding opaque/accessible treatments. Printing hides decoration and uses readable surfaces.

The account greeting uses the authenticated account and school records; it does not use one shared generic account name. These changes apply through the shared dashboard code without recreating existing accounts or requiring a setting for each school.

## Install

1. Back up application files and database.
2. Open the ZIP link and use GitHub’s **Download raw file** button.
3. Upload and install through **Platform Admin → Core updates**.
4. Refresh an existing account’s dashboard and try both themes. A browser tab retaining older assets may need a reload.

This cumulative ZIP contains 34 approved application files plus `release.json`. It includes the preceding admissions and glass updates. It adds no configuration, credentials, database tables, paid services or external artwork/fonts. Compared with 5.3.29, six files change: the shared welcome renderer, admissions presentation renderer, shared CSS/JavaScript, asset versions and core version. Admissions processing, payments and account permissions are not changed.

The shared personal welcome is on the home dashboard. Individual working pages continue to use their task-specific headings, rather than repeating a large personal greeting on every form. The public website, login page and standalone live-class player are outside this dashboard styling update.

Animation is restrained, uses CSS transform/opacity for the background, and has no background network requests. Smaller screens retain the lighter blur from 5.3.29. Actual animation smoothness depends on the browser/device; reduced motion is supported directly.

[Validation](SchoolOS_5.3.30_Validation.md) · [Archive checksum](SchoolOS_5.3.30_SHA256SUMS.txt)

Validated locally with fictional role accounts. This session did not install the update on the hosted school.
