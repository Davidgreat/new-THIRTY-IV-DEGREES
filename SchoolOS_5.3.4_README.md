# School OS 5.3.4 — Learning Studio

This cumulative core update adds a calmer classroom workspace and teacher-led interaction to the existing central LiveKit integration. It retains the earlier audit repairs, class notifications, sound controls, Employment menu buttons and platform-wide media settings.

## What happens when a class stops?

| Action | What everyone sees | Can the same lesson restart? |
|---|---|---|
| Teacher leaves / loses connection | Learner media stops; the lesson can be started again | Yes, within the joining window |
| Pause class | Everyone disconnects; the lesson is marked paused | Teacher selects Reactivate lesson, then starts it again |
| End session | Everyone disconnects; lesson moves into collapsed Past lessons | Teacher can reactivate before the scheduled finish |
| Permanently close | Lesson moves into Past lessons for teacher and learners | No; schedule a new lesson |
| Scheduled finish passes | Joining closes and the card moves into Past lessons | No; schedule a new lesson |

Joining opens 15 minutes before the scheduled start and closes at the scheduled finish. Reactivation does not extend the finish time. Older ended lessons can also be reactivated if still within that window and not permanently closed. Students can rejoin after the teacher starts the reactivated classroom. Past lessons are collapsed by default so completed cards do not occupy the current lesson area. Discussion remains attached to the lesson across a pause/restart.

Schedule new lessons with a **30, 60, 90, 120, 150, 180, 210 or 240 minute** duration. Cards show a live countdown to the scheduled start, then the time remaining. Times are West Africa Time. The active classroom also shows time remaining.

## Inside the classroom

- A responsive green-and-cream Learning Studio with teacher video, expandable room, discussion/people/quick-check panels and distinct controls.
- **Share screen** switches to **Stop sharing screen**, then returns to the camera. Browser-level stopping also restores the camera. Screen sharing, amber Pause and red End session are separate buttons. The teacher can mute their own microphone independently.
- Class chat and questions stay in the active room. They do not open school chat or navigate away. Messages are limited to 1,000 characters and the panel shows the most recent 60 chat/question/reaction events. This is a lesson discussion, not a permanent complete transcript viewer.
- Learners can raise/lower a hand. The People panel orders raised hands by request time, and the teacher can select an online learner to speak.
- Listen mode starts with learner publishing disabled. Inviting one learner revokes the other learner publishing permissions at the media server before granting microphone-only permission to the selected learner. Open discussion allows all learners to choose to speak. Listen mode revokes learner publishing again. Learner cameras and screen sharing remain prohibited.
- A student chooses **Enable microphone to speak** and accepts browser permission on their first speaking opportunity. After that consent, a new speaking invitation can enable their microphone automatically while this classroom session remains open. Students can mute themselves. Browsers and operating systems retain their own microphone permission controls; teachers cannot silently bypass them. Rejoining starts with a fresh consent state.
- Four reactions: applause, understanding, encouragement and a request for explanation.
- A teacher can share a **single-question multiple-choice quick check** with two to four options. Each learner submits one answer; duplicate retries do not change it. The teacher sees response totals. Correctness is withheld from the learner API and interface until the teacher closes the check. This is a formative classroom activity, not an examination engine or automatic report-card grade. Starting another quick check replaces the active one.

Lesson access is checked against the authenticated school, current class/session and allocated teacher. Interaction requests require a current classroom peer session and CSRF token. Learners cannot moderate the floor, create checks or end lessons. Restarts rotate media room names so previously issued room tokens target the old room. These checks do not replace protecting provider administrator credentials.

## Requirements and installation

1. Back up application files, database and matching private encryption keys outside the web root. End active built-in classes and test the update on staging.
2. Install **SchoolOS_5.3.4_Learning_Studio_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**, not the plugin installer.
3. Confirm version **5.3.4** and reload all portal tabs.
4. Existing central LiveKit settings remain saved. Check **Setup & account → Platform live classrooms → Test central media API**. No credentials need to be copied into this ZIP or GitHub.
5. Test a scheduled lesson with the teacher and at least two enrolled students on separate devices/networks. Check both one-speaker and open-discussion audio, permission denial, pause/reactivation, screen start/stop, chat, quick checks and permanent closure.

No database schema migration is required. The update uses existing Portal Experience/Experience tables, which must already be activated. It preserves configuration files, student records and uploads. It does not purchase a service or change provider billing.

**Student speaking requires the configured LiveKit-compatible media service.** Direct peer-to-peer fallback keeps its eight-person limit and teacher-only audio. Chat, questions, reactions, hands and quick checks remain available inside the direct classroom. External Meet/Zoom invitations continue to use the external provider's meeting interface and controls.

Test with real school accounts connected to your central LiveKit service. The isolated public demo does not inherit live media credentials and needs its own dedicated media configuration; otherwise its direct fallback cannot offer learner microphones.

The PHP portal can remain on shared cPanel. The media service still needs its own compatible hosted project or server. Provider capacity/usage allowances remain applicable. See the [free-hosting research report](SchoolOS_Free_Live_Class_Research.md).

## Validation and limits

Validation covers actual local LiveKit audio/video and microphone permission changes, chat/questions/reactions, raised hands, quiz-answer privacy, desktop/mobile controls, pause/rejoin, archival, server-side duration validation, cross-school/role rejection and installer recovery/rollback. Media uses synthetic test cameras/audio; screen-share UI/media plumbing uses a synthetic captured board. The production desktop picker, mobile screen-capture support, actual school internet networks and provider-scale load still require acceptance tests. Collaboration and presence refresh by polling, normally about every 2.5 seconds; they are not instantaneous browser push.

The software keeps the most recent 300 scoped lesson cards, with current lessons prioritised. Larger archives are not a searchable full historical report. Classroom chat and formative checks remain stored in the existing school database; no recording is added.

See the [validation summary](SchoolOS_5.3.4_Validation.md) for the completed checks.

## Rollback

End all classrooms before rollback. Use the updater's recorded backup to restore the previous files; it does not restore database history. Version 5.3.3 does not understand the new paused/archived workflow or classroom interactions. Restore a consistent protected database backup with its matching files if reverting lifecycle behavior; do not resume classroom operations with mismatched application/database state. The older finance-encryption rollback caveat applies when reverting as far as 5.3.0.
