# School OS 5.3.2 — live-class notifications, sound and full-class video

Installable maintenance update for the previously supplied School OS 5.3.1 installation. Includes the prior 5.3.1 repair files as well as the new features. No live website changes have been made by publishing this ZIP.

## What changes

- Students receive in-platform notices when their class is scheduled, a 15-minute reminder, a live status notice and an ended/cancelled status notice. The class link opens the correct lesson card. Notices are scoped to the student's verified class and current session. Teachers see their own scheduled classes.
- An expandable notification inbox shows unread counts and lets each account mark notices as read. Read status survives reloads and is stored in the existing account progress table. A changed class time or status becomes a fresh unread notice. The inbox includes currently relevant notices, not a permanent event-history archive: classes in the next 30 days/recently ended classes, recent school announcements, assignment deadlines, published results and existing chat/family/operational alerts. Up to 80 current items are returned per refresh.
- Notification tones and successful-save beeps use Web Audio. Sound preference is remembered separately for each account. A save beep is triggered only after a server-confirmed success, not merely when the submit button is pressed. Browsers require a click/tap to unlock audio; select **Enable sound** once. Muted devices, browser policies and OS settings still apply. If autoplay is blocked after navigation, the queued success tone plays on the next interaction. Notifications refresh while a portal page is open, normally within 15 seconds. This is not an off-site browser push/SMS/email service.
- Teacher Employment menus are separated, wrapping buttons with hover, focus and active states. Links retain the Employment route. Shared form/table styles and HR save-confirmation messages now work on that standalone page.
- Optional built-in full-class media-server mode removes the eight-person application cap. The teacher publishes to a LiveKit server; enrolled learners subscribe without requesting learner cameras/microphones. A bundled, pinned LiveKit client avoids a runtime third-party SDK download. Server credentials are encrypted in the school's existing secret store. Short-lived room-scoped learner tokens prohibit publishing.
- Existing direct peer-to-peer broadcasts remain available as an eight-person fallback until a media server is configured. Existing active broadcasts keep their selected transport. **This update does not turn peer-to-peer broadcasting into an unlimited service and does not provision a media server or hosting plan.**

## Installation

1. End active live classes and back up application files, MySQL database and private encryption keys outside the public web root. Use a staging copy first.
2. Sign in as **Platform Super Admin → Updates & Plugins → Core updates**.
3. Upload **SchoolOS_5.3.2_Classroom_Notifications_Update.zip** directly, confirm the backup/trusted-source checkbox and install. Do not use the plugin installer or upload this README/evidence archive.
4. Confirm version **5.3.2**, then reload open portal pages. Shared scripts/styles use a new cache version.
5. Existing Experience/Portal tables must be activated. No database migration runs during ZIP installation; notification read state uses `xp_progress`, and media settings use the existing encrypted `sv_settings` table.
6. Schedule a test class as the allocated teacher. As a student in that class, check the updates area and **All notifications**. Test **Mark read**, refresh and verify it remains read. Another class must not receive the notice. Announcements use the existing audience/recipient rules.
7. Click **Enable sound** in the updates area. Confirm its test tone, save a study task or another supported form, and verify the success beep. Error responses should not beep as successful saves. Turn sound off to mute both notification and save tones.

## Enable full-class SchoolOS Live

As a live **school administrator**, open **Learning → Live → Full-class SchoolOS Live media server**.

1. Create/use a dedicated **LiveKit Cloud** project, or deploy a production **self-hosted LiveKit** server with a valid TLS certificate, HTTPS/WSS signalling, correctly advertised public media addresses and required media/relay firewall ports. The standard PHP/cPanel web host alone does not provide this media server.
2. Enter its `wss://...` server URL, API key and API secret in the secure admin form. Do not paste credentials into GitHub or chat. The URL must be the server origin, without a path, query or credentials. Use the provider's actual API key and secret; they are not the end-user room token.
3. End existing built-in broadcasts before changing media-server settings. Save the settings, schedule or restart a new lesson, and test with a teacher and learners on separate internet networks.
4. In media-server mode, School OS does **not** impose the eight-person cap. Actual participant capacity, traffic costs, reliability and limits depend on your server sizing/hosting plan. Choose capacity for your real class size; no system has literally unlimited resources.
5. Test teacher camera/audio, student reception, reconnects, screen sharing and **End lesson**. End lesson calls the media service to delete the room and disconnect its participants. If that shutdown request fails, School OS reports the failure so the host can retry rather than falsely reporting a completed shutdown.
6. Use separate credentials/server capacity for a public demo. The live school's credentials are not automatically copied to the isolated demo; demo use requires its own platform-managed configuration. This update's live-school setup form deliberately rejects changes from the shared public sandbox.

LiveKit client 2.24.0 is bundled in the approved `classroom.js` payload with third-party licence notices. No API secret is included in the ZIP or client bundle.

## Validation performed

- One teacher and **nine students simultaneously** received real video/audio through a local LiveKit 1.13.11 server with a TLS proxy and TCP TURN. The teacher used one WebRTC connection; students made no camera/microphone requests. End lesson deleted the room and disconnected every learner. This is a functional test beyond eight participants, not a production load/network guarantee.
- Browser checks passed for separate Employment buttons on desktop/mobile, correct active navigation, real Web Audio tone playback, save-success beeps, notification beeps, remembered sound settings and persisted read state.
- Scoped notification/reminder/read-state/token-permission tests passed. Syntax and role-navigation checks passed; installation, injected-failure recovery and rollback were checked against the existing updater.
- Test with your own devices and production media credentials before school-wide use. Your actual provider account, internet networks, large-class capacity and mobile-browser screen-sharing matrix were not tested here.

## Rollback

End every SFU/media-server lesson before a file rollback; the older client cannot manage media-server rooms. Restore the previous release using Updates & Plugins' recorded backup ID. Settings/read-state rows remain, and no schema is removed. The existing 5.3.1 warning still applies when rolling back further to 5.3.0: older Finance code cannot read school payment keys re-saved in encrypted form under 5.3.1+.

See `SchoolOS_5.3.2_SHA256SUMS.txt` for package integrity. SHA-256 is an integrity check, not a digital publisher signature.

Package SHA-256: `532d5137f02665898e6c06478c823c31dfd5532acd98d0a8d6688f3f3dcf75c0`
