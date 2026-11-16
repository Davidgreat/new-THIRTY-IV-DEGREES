# School OS 5.3.34 — Automatic background playback

[Download the installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.34_Background_Autoplay_Update.zip)

The desktop background now starts automatically using the motion-recovery logic from 5.3.33. The Play/Pause background button is removed entirely.

## Behavior

- Desktop circles and colour cycling start without a click, including when the PC reports reduced motion. This automatic override applies only to the decorative desktop background; other interface reduced-motion behavior is unchanged.
- Earlier saved background pause choices are no longer read and cannot stop autoplay. No browser preference setup is required after installation.
- Independent startup and the stalled-frame watchdog/timer recovery remain in place.
- Hidden tabs pause and resume automatically. Printing and display preferences that hide the decorative scene still stop it.
- The mobile size, speed, colour/collision profile and mobile reduced-motion behavior are unchanged. No background playback button is created on any dashboard.

The larger desktop circles, wide movement, native hover effects, personal welcomes and preceding school-feature updates remain included.

## Install

1. Back up application files and database.
2. Open the ZIP on GitHub and choose **Download raw file**.
3. Install through **Platform Admin → Core updates**.
4. Refresh the dashboard. The background starts automatically; no Play button or Windows setting change is needed.

This cumulative ZIP contains 34 approved application files plus `release.json`. Compared with 5.3.33, only `portal_experience.php`, `portal_experience.css`, `portal_experience.js` and `VERSION.txt` change. It adds no configuration, credentials, tables or paid services and does not change school transactions or account permissions. The existing uncached asset route uses a new version reference for the updated CSS/JavaScript.

[Validation](SchoolOS_5.3.34_Validation.md) · [Archive checksum](SchoolOS_5.3.34_SHA256SUMS.txt)

Validated locally. This session did not install the update on the hosted school.
