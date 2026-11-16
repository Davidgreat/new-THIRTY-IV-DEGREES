# School OS 5.3.33 — Desktop background motion recovery

[Download the installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.33_Desktop_Motion_Recovery_Update.zip)

[Reproduction and Play/Pause preview — MP4](SchoolOS_5.3.33_PC_Play_Background_Demo.mp4) · [Desktop Play control](SchoolOS_5.3.33_play_control.jpg)

This update addresses conditions that can leave the PC background stationary even though it moves in a recording or on another device. It adds a clear desktop Play/Pause control, isolates animation startup, and recovers from a stalled browser animation-frame loop. The exact condition on the user's PC was not remotely confirmed.

## Use it on the PC

1. Back up files and database, then install the ZIP through **Platform Admin → Core updates**.
2. Refresh the dashboard.
3. Look beside **School chat** in the role strip near the top of the dashboard.
4. If the button says **Play background**, click it. When the circles are enabled it changes to **Pause background**.

No Windows setting change is required. The choice is saved locally for the current account/browser when browser storage is available. It does not create a school-wide setting or change another account's motion preference. Clicking Pause stops the decorative movement and colour cycling. A page reload keeps the saved choice.

## What was changed

- **Reduced-motion handling:** Computer/browser preferences can intentionally stop the preceding animation. The control explains this in its title and allows an explicit desktop-only choice to play the background. This overrides reduced motion for the background circles only; other interface reduced-motion behavior remains respected.
- **Independent startup:** Background initialization now runs before the other shared dashboard helpers. A later helper error cannot prevent the animation from starting. The module contains its own startup failure and exposes a clear unavailable status rather than leaving an empty control.
- **Stalled-frame recovery:** If an enabled desktop background is not advancing through its normal frame callbacks, a watchdog switches to a timer-based animation driver. Hidden tabs, print, reduced transparency and forced-colour display still suspend the simulation. Resume resets timing to avoid a large jump.
- **Mobile preserved:** The new control is hidden on phone-sized layouts. Desktop Play/Pause choices do not override the mobile behavior. The existing mobile size, speed, colours and collision profile are retained; the desktop watchdog is not started on mobile.

The larger PC circles, wide travel and native CSS hover effects from 5.3.32 remain included. The shared CSS/JavaScript use a new version reference through the existing uncached asset route.

If the control shows **Background hidden**, display preferences are hiding the decorative scene and the control is disabled. **Background unavailable** indicates a contained startup problem; reload the page to retry. These states provide information for follow-up rather than assuming every stationary background has the same cause.

## Package scope

This cumulative ZIP contains 34 approved application files plus `release.json`. Compared with 5.3.32, only `portal_experience.php`, `portal_experience.css`, `portal_experience.js` and `VERSION.txt` change. No database tables, credentials, configuration, permissions or school transaction handlers are changed. The desktop control stores its preference in the browser rather than sending a server request.

The preview records a local browser with reduced motion deliberately enabled: the scene starts stationary, Play starts it, Pause stops it, and Play resumes it. It uses fictional account records. Preview files are repository documentation and are not installed into the application.

[Validation details](SchoolOS_5.3.33_Validation.md) · [Archive checksum](SchoolOS_5.3.33_SHA256SUMS.txt)

Validated locally. This session did not install the update on the hosted school or inspect the user's actual PC settings.
