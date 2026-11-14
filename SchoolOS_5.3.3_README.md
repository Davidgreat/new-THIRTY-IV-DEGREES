# School OS 5.3.3 — one platform media setup for all schools

This cumulative update keeps the 5.3.1 repairs and 5.3.2 class notifications, sound, Employment-menu fixes and native SFU client. It moves the default media configuration to **Platform Super Admin → Setup & account → Platform live classrooms**.

## What changes

- Super Admin saves one LiveKit-compatible WSS origin, API key and encrypted API secret. Every live school inherits that service automatically. Self-hosted LiveKit is supported; a paid LiveKit Cloud subscription is not required.
- Super Admin can optionally configure one shared TURN relay for the direct fallback, and run a read-only media API connection test. The full-class server has its own media/relay configuration; the optional fallback relay does not replace it.
- School Admin sees the central-service status and does not need provider credentials. The old school settings endpoints reject edits unless Super Admin explicitly enables optional school overrides.
- Rooms and short-lived tokens remain separated by installation/database, school and lesson. Sharing a server does not merge classrooms or student lists.
- A shared-settings change is blocked while built-in broadcasts are active, preventing the service from changing underneath a class. Host-start and configuration operations serialize; ordinary student joins do not take the platform settings lock.
- Optional policy **Shared server; allow optional school overrides** permits an explicitly saved override for a school. Old saved school keys do not silently override the central service. A school can choose **Use central platform service** again.
- **Disable media-server mode** keeps the direct fallback and external invitations available without deleting encrypted credentials. The direct fallback remains an eight-person mode; native full-class mode follows actual server/provider capacity.
- Existing per-school configuration is preserved for continuity before the first platform policy is saved. No school key is automatically promoted to platform-wide use. An idle direct lesson can adopt the central server when its host starts it afresh.
- The separate public demo database does not inherit live-platform credentials or room names.

## Install

1. Back up files, MySQL database and private encryption keys outside the web root. End active built-in broadcasts and use a staging copy first.
2. **Platform Super Admin → Updates & Plugins → Core updates**: upload **SchoolOS_5.3.3_Central_Classroom_Update.zip** directly. This is not a plugin package.
3. Confirm installed version **5.3.3**, then reload open portal pages. The release contains approved application files and a SHA-256 manifest; it does not overwrite config.php, credentials, student records or uploads. It runs no schema migration. Existing Experience/Portal tables must be activated.
4. Open **Setup & account → Platform live classrooms** as Platform Super Admin.
5. Select **Shared server for every school**, enter the server origin, API key and API secret once, and save. The fields deliberately do not display stored credentials. Blank fields retain existing values; changing an origin/key requires re-entering the secret.
6. Click **Test central media API**. This validates the server API/TLS/authentication connection without creating a classroom. It does not prove browser media connectivity or provider capacity.
7. As an allocated teacher, schedule/start a lesson. As a student from that school/class, verify moving video and audio on another internet connection, notification/reminder delivery, reconnect and End lesson. Check that a different school/class cannot join.
8. Verify **Enable sound**, confirmed-save beeps and the separated teacher Employment buttons. Sound still requires an initial browser click/tap and an unmuted device.

## Your shared cPanel hosting

The PHP portal can stay on shared cPanel. The persistent native media service generally cannot run there. Choose a separate compatible server or hosted project and confirm outbound HTTPS from cPanel plus browser access to its signalling/media ports.

Read **[the free live-class research report](SchoolOS_Free_Live_Class_Research.md)** before choosing hosting. It compares free software, limited free hosted plans, external free meetings and free-VM constraints. The existing Google Meet invitation option can be used immediately when its meeting limits fit your lessons.

This update does not purchase or provision hosting and does not contain a Cloudflare/Daily/Jitsi/YouTube native adapter. The configuration form accepts the LiveKit-compatible service already implemented and tested in School OS; other provider protocols require their own integration.

## Operational details

Central API secrets use the existing encrypted `v23_secrets` store and private `storage/system/v23-key.php`. Existing optional school secrets use their existing storage/key. Back up the matching private keys with the database. Keep provider secrets out of GitHub and screenshots.

All live schools sharing a hosted project also share that project's quotas and bill. The application does not create a free quota per school, measure the provider's bill, or turn a paid plan into a free plan. Use the provider dashboard and the dated research report to choose a plan/allowance.

The isolated demo requires dedicated configuration in its own database; live credentials are intentionally not copied into the public sandbox. Existing dedicated demo school configuration remains usable through the legacy inheritance path. A platform operator can provision a dedicated demo service if desired.

## Rollback

End all native media-server lessons before rollback. The updater restores verified previous files, not settings or database history. A 5.3.2 rollback does not understand the new central settings: before resuming native classes under 5.3.2, provide the appropriate per-school settings or restore a consistent protected settings backup. Retained prior school keys are not deleted by this update. The older 5.3.0 encrypted-Finance-key caveat still applies when rolling back further.

## Validation

The release was tested with encrypted central configuration, role enforcement, blank-field retention, optional overrides, shared fallback relay, inactive-lesson transport adoption, cross-school room/admission separation, demo database isolation, actual Super Admin UI save/test and school read-only UI. Real video/audio worked with a central-only server configuration and a teacher plus nine students. Notification/sound and teacher Employment UI tests were repeated, as were role-page rendering and installer recovery/rollback checks. These are local integration tests, not production provider/hosting acceptance or a large-scale load test.
