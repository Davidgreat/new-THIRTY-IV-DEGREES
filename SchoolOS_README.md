# School OS downloads

## Latest: 5.3.5 — automatic classroom waiting room

[Download the installable School OS 5.3.5 update](SchoolOS_5.3.5_Waiting_Room_Update.zip?raw=true)

[Installation guide](SchoolOS_5.3.5_README.md) · [Validation summary](SchoolOS_5.3.5_Validation.md) · [Learning Studio guide](SchoolOS_5.3.4_README.md)

A student arriving before the teacher sees a waiting prompt. The classroom checks for readiness and automatically connects actual audio/video when the teacher starts, without another Join click. Waiting checks do not consume repeated admission attempts or participant slots. Leave cancels automatic entry; closed/expired lessons stop waiting.

Works with both configured LiveKit and direct fallback. Retains Learning Studio chat, questions, reactions, quick checks, speaking invitations, pause/reactivation, collapsed Past lessons, durations/countdowns, central media settings, notifications, sounds and earlier repairs.

Back up files, database and private keys, end active classes, test on staging, then install through **Platform Super Admin → Updates & Plugins → Core updates**. Confirm 5.3.5 and refresh all teacher/student tabs. Saved accounts and media settings remain in place; no schema change is required. The isolated demo still uses separate media settings.

Validated locally: 14 browser waiting checks with actual video/audio in both transports, five server authorization/admission contracts, 15 Studio workflow checks and five installer/recovery/rollback checks. Actual school networks, production provider capacity and browser autoplay policies still need acceptance tests.

SHA-256: `fbcfe3d252794451da5faecaf215ca57f316643f88c705c820cfa0a84100ace1`

## Previous releases and research

[5.3.4 Learning Studio](SchoolOS_5.3.4_Learning_Studio_Update.zip?raw=true) · [5.3.3 central configuration](SchoolOS_5.3.3_Central_Classroom_Update.zip?raw=true) · [5.3.2 notifications](SchoolOS_5.3.2_Classroom_Notifications_Update.zip?raw=true) · [5.3.1 audit repairs](SchoolOS_5.3.1_Audit_Update.zip?raw=true)

[Free live-class hosting research](SchoolOS_Free_Live_Class_Research.md). Provider allowances/capacity apply; student audio needs configured full-class mode and browser consent. Direct fallback remains limited to eight participants with teacher audio.
