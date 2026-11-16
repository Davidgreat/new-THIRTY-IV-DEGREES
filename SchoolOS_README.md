# School OS 5.3.32 — Desktop motion and hover

[Download the installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.32_Desktop_Motion_Update.zip)

[Desktop motion preview — MP4](SchoolOS_5.3.32_desktop_preview.mp4) · [Dark screenshot](SchoolOS_5.3.32_dark_preview.jpg) · [Light screenshot](SchoolOS_5.3.32_light_preview.jpg)

The mobile circles keep the size, speed, transparency and colour cycle from 5.3.31. The new visual rules apply at desktop widths of 851px and above. Narrower windows continue to use the mobile profile.

## Desktop changes

- **Larger circles:** Desktop circles can reach 650px across, restoring the larger background shapes. The mobile sizing formula is unchanged.
- **Wide travel:** A larger movement area extends beyond the visible content, allowing the big circles to travel across the background, move partly off-screen and return. Elastic collisions push circles apart. The simulation no longer confines oversized circles to a tight visible rectangle.
- **Clearer colour changes:** Desktop blend cycles are approximately 3.8–5.2 seconds. Mobile retains the previous 6–8 second cycles. Transparency stays the same.
- **Native hover:** The Applications tab and other desktop buttons/menus now use direct CSS `:hover` rules. A coloured highlight, 7% enlargement, stronger glow and outward breathing outline are visible without relying on the JavaScript pointer handler. The hover rules do not depend on the browser identifying its pointer as a fine-pointer device.
- **Stable clicking:** Enlargement settles after its short transition; the continuing breathing effect expands the outline rather than continuously moving/resizing the clickable target.
- **Fresh assets:** Dashboard CSS and JavaScript load through fixed, uncached PHP asset routes with new version references. This avoids reusing the preceding static asset URL. Only the two public dashboard asset files can be served by this route; it does not expose arbitrary files or start an application session/database connection.

Reduced-motion preferences still stop the decorative movement and hover enlargement. Touch behavior, the restored personal greetings and school workflows remain included. The hosted PC's exact previous cache state was not confirmed; fresh asset loading is a protective change, not a claim that caching was proven to be the cause.

## Install

1. Back up the application files and database.
2. Open the ZIP link and select **Download raw file** on GitHub.
3. Install through **Platform Admin → Core updates**.
4. Refresh the PC dashboard. No extra school configuration or account recreation is required.

The cumulative archive contains 34 approved application files plus `release.json`. It includes the preceding admissions, welcome and glass updates. Five files differ from 5.3.31: `index.php`, `portal_experience.php`, the shared dashboard CSS/JavaScript and `VERSION.txt`. No configuration, credentials, new database tables or paid services are added. Admissions processing, finance handlers and account permissions are unchanged.

The preview is a recording of the local desktop implementation with fictional account records. The video and screenshots are repository documentation outside the installable ZIP.

[Validation](SchoolOS_5.3.32_Validation.md) · [Archive checksum](SchoolOS_5.3.32_SHA256SUMS.txt)

Validated locally. This session did not install the update on the hosted school.
