# School OS 5.3.31 — Bubble motion and visible hover feedback

[Download the installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.31_Bubble_Motion_Update.zip)

[Motion preview — MP4](SchoolOS_5.3.31_motion_preview.mp4) · [Dark screenshot](SchoolOS_5.3.31_dark_preview.jpg) · [Light screenshot](SchoolOS_5.3.31_light_preview.jpg)

The background circles retain the transparency from 5.3.30, with their blur removed so colours and edges are clearer. They now travel visibly around the dashboard and bounce apart when they meet. Hover feedback also covers ordinary text links, with stronger rings and glows on buttons and menus.

## Changes

- **Clearer circles:** No blur filter on the background bubbles or the decorative banner circles. The working glass panels keep their frosted finish. Circle transparency remains at approximately 22–23%.
- **Visible movement:** A small local simulation moves the three background bubbles within the visible content area. Their sizes adapt to the viewport. They bounce off the boundaries and use elastic collision responses to separate after contact, rather than passing through one another.
- **Quicker colour shifts:** A contrasting gradient fades in/out over 6–8 second cycles. Each bubble has its own phase. The circles stay transparent while their colours change.
- **Stronger hover feedback:** Buttons, menu items and actionable cards receive a visible outline/glow and a small lift. The outline pulses while the target stays stable enough to click. Ordinary text links get a stronger underline and text glow. Existing card shadows no longer hide the feedback.
- **Dynamic menus:** Delegated pointer/focus handling also covers links and buttons inserted by existing dashboard refreshes. It does not intercept clicks or change their destinations.
- **Touch and keyboard:** Touch devices avoid sticky hover effects; keyboard focus has a steady visible ring. Disabled controls are excluded from the new hover feedback.
- **Motion preferences:** Reduced motion freezes the bubbles at separated positions and stops colour/hover animation. The simulation pauses in hidden tabs, print view, reduced-transparency mode and forced-colour mode. It resumes without advancing through the whole hidden interval.

Background animation is capped at roughly 30 updates per second. It uses three local elements and does not add network traffic or an animation library. Actual smoothness depends on the device and browser. Collision movement applies to the decorative background bubbles; the dashboard's working layout stays organized.

The personal welcomes restored in 5.3.30 remain included. This release changes styling, decorative movement and interaction feedback; it does not change school transactions, account permissions or admissions processing.

## Install

1. Back up application files and database.
2. Open the ZIP on GitHub and choose **Download raw file**.
3. Install through **Platform Admin → Core updates**.
4. Refresh the dashboard. The new stylesheet and JavaScript both use a new cache version.

The cumulative ZIP contains 34 approved application files plus `release.json`. Only four files differ from 5.3.30: shared dashboard CSS, shared dashboard JavaScript, the asset-version references and `VERSION.txt`. No database tables, configuration, credentials, external artwork or paid services are added. Existing accounts use the effects through the shared dashboard shell; no per-school configuration is required.

The motion preview is a recording of the local implementation with fictional account data, not a separate animated mockup. It shows bubble movement, colour changes and hover feedback in both themes. The preview files are repository documentation and are not installed into the application.

[Validation details](SchoolOS_5.3.31_Validation.md) · [Archive checksum](SchoolOS_5.3.31_SHA256SUMS.txt)

Validated locally. This session did not install the update on the hosted school.
