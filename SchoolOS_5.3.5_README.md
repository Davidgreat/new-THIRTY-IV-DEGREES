# School OS 5.3.5 — automatic classroom waiting room

This cumulative core update fixes the blank/inactive screen when a learner clicks Join before the teacher starts. It retains Learning Studio, central LiveKit configuration, speaking controls, chat, quick checks, notifications and earlier repairs.

## New behavior

1. An allocated learner clicks **Join classroom** during the lesson's existing joining window.
2. If the teacher has not started, a visible **Waiting for your teacher** screen explains that connection will happen automatically. The learner's camera/microphone stay off. Classroom discussion controls stay hidden until admission.
3. The page checks approximately every three seconds while open. Waiting checks do not repeatedly consume the Join retry limit, create peer sessions or take up direct-fallback participant slots.
4. When the teacher's camera/audio setup is ready, the page automatically admits the learner and connects media. The learner does not click Join again.
5. **Leave classroom**, switching to another lesson, or closing the page cancels waiting. A late response cannot reconnect a learner who has left. A temporary network interruption keeps retrying while the page remains open.
6. Ending, pausing, cancelling, permanently closing or expiring the lesson stops waiting and shows a message. Waiting does not silently reopen a closed session. Reactivated lessons still use the existing Join workflow.

This works with both configured LiveKit full-class mode and the eight-person direct fallback. External Google Meet/Zoom waiting behavior remains controlled by those providers. Waiting learners receive no media token or peer key until the teacher is ready. Class/session/tenant authorization, CSRF checks and the 15-minute early-entry/scheduled-finish window still apply.

Browsers may slow polling in background tabs or require pressing Play for sound. Keep the classroom tab open; automatic admission does not bypass browser media policies. This is an in-platform waiting screen, not an offline push notification or a teacher-managed approval queue. Waiting learners do not appear in the connected-participant roster until admitted.

## Install

1. Back up files, database and matching private encryption keys. End active classes and test on staging.
2. Upload **SchoolOS_5.3.5_Waiting_Room_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm version **5.3.5**, then reload teacher and student portal tabs. Refreshing is required so both sides use the new media-ready handshake, including direct fallback.
4. Sign in as a student and join a scheduled lesson before its teacher. Confirm the waiting prompt.
5. Start the same lesson as the teacher and allow camera/audio access. The student should automatically receive video/audio without another Join click.
6. Repeat with Leave while waiting, and with the teacher ending a lesson before starting it.

Existing accounts, central LiveKit settings, classroom data and uploaded files remain in place. No database schema change, account recreation, media-service purchase or provider billing change is required. Existing demo accounts also receive this interface; the isolated demo still needs its own media configuration for full-class/student-audio features.

See the [5.3.4 classroom guide](SchoolOS_5.3.4_README.md) for lifecycle, microphone consent, quick checks and other Learning Studio features. Provider capacity and browser/device limits remain applicable.

## Validation

Local tests cover waiting before a teacher, waiting through a delayed media-permission step, automatic reception of actual teacher video/audio in LiveKit and direct mode, waiting longer than the old retry budget, cancellation with an in-flight response, temporary network loss, closure while waiting, and scoped server authorization. Media tests use synthetic camera/audio devices and local TLS/TURN infrastructure, not the school's production internet connections. Installer failure recovery, deployment and rollback are checked against the existing updater.

See the [validation summary](SchoolOS_5.3.5_Validation.md) for the completed checks.

## Rollback

End classes before rolling back. Restore the previous version through its recorded updater backup and reload all classroom tabs. This update makes no schema changes; the previous 5.3.4 behavior returns, including requiring a second Join attempt if the learner arrives before the teacher. For older rollbacks, follow the matching release's database/lifecycle and encryption caveats.
