# School OS 5.3.7 — mobile waiting-room fit

Fixes the live-class waiting panel extending beyond a phone's screen and forcing the user to zoom out.

The phone layout now lets the waiting prompt size to its text instead of inheriting a video aspect ratio and fixed minimum height that forced a roughly 462-pixel panel. Text, captions and controls wrap within the available width. The classroom page header can also wrap its controls on narrow screens. Browser zoom remains available; no viewport/zoom restriction or page-wide clipping is added.

Automatic student entry when the teacher starts, account-aware wording, classroom media controls and all earlier features are retained. The stylesheet URL is refreshed so browsers can load the corrected layout after installation and page refresh.

## Installation

1. Back up application files, database and private encryption keys; end active classes and test on staging.
2. Install **SchoolOS_5.3.7_Mobile_Waiting_Room_Update.zip** via **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.7** and refresh the classroom page on the phone. If an old tab still shows the previous layout, close and reopen that tab.

Existing accounts, saved LiveKit settings and classroom data remain in place. No schema migration is required.

## Checks

Browser checks passed for waiting and left-room states at 320×568, 360×740, 390×844 and 430×932 phone sizes, 740×360 landscape and 1440×900 desktop. Each had page width equal to viewport width, normal zoom and the prompt text contained within the panel. Normal vertical page scrolling remains available on shorter screens. These are emulated Chromium viewports; verify the layout on your actual phone/browser too.

Changed PHP syntax, package file hashes, installation, injected-failure recovery, repeated-install refusal, rollback and traversal rejection passed. This release changes layout and the stylesheet cache URL; media/automatic-admission code is retained.

Rollback: end classes, restore the updater's recorded 5.3.6 backup and refresh portal pages. The earlier mobile layout will return; no database changes are added by this release.
