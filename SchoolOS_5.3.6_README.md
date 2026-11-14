# School OS 5.3.6 — account-aware welcome messages

This cumulative core update makes the dashboard and live-classroom introductions fit the signed-in account and its assigned responsibilities.

## What changes

- Welcome headings use the account's full saved name. For example, **Demo Teacher** and **Demo Student** no longer both greet only “Demo”. Existing account names are preserved.
- Teachers see **Your classes. Your teaching day.** on the dashboard and **Room to teach.** in the live-classroom area. The description refers to their learners and lessons.
- Students see **Your next discovery starts here.** and **Room to learn.**, with wording about their teacher, classmates, homework and results.
- School administrators see their school-management priorities and **Room to connect.** for school live classrooms.
- Parents/guardians, Platform Super Admin, Admissions and Partner accounts have their own welcome descriptions and readable account-role labels.
- Staff introductions follow the capabilities actually assigned to that account in its school: HR/payroll, transport, driver duties, boarding, library, stock, procurement, assets, communications or website work. Accounts with several assigned responsibilities list those responsibilities together. Staff without specialist assignments get a tasks-and-conversations introduction.

These are account-aware introductory messages. Existing class notices, conversation membership and notification read state continue to use their existing account/class/recipient checks. School-wide announcements still appear to their intended shared audience.

This update retains the automatic waiting room, Learning Studio, central LiveKit configuration, notifications/sounds, classroom chat and speaking controls, and previous audit repairs. It does not change account permissions or require a database migration.

## Installation

1. Back up files, database and private encryption keys; end active classes and test on staging.
2. Upload **SchoolOS_5.3.6_Account_Messaging_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.6** and refresh the dashboard/classroom pages. Existing live and demo accounts receive the new wording without recreation. Saved central media settings remain in place.
4. Review the teacher, student and staff dashboards to confirm each description matches that account's responsibilities.

Validation: dashboard rendering was checked with 14 account profiles, including specialist and multiple-capability staff accounts; teacher/student/admin live-classroom introductions were checked. All 589 role-page checks passed without HTTP/PHP rendering failures. Changed PHP syntax, installer deployment, failure recovery, same-version refusal, rollback and traversal rejection also passed.

For classroom operation and browser/media requirements, see the [5.3.4 Learning Studio guide](SchoolOS_5.3.4_README.md) and [5.3.5 waiting-room guide](SchoolOS_5.3.5_README.md).

## Rollback

End active classes, use the updater's recorded backup to return to 5.3.5, then refresh pages. This restores the earlier welcome wording; this release adds no schema or account-data changes. For earlier rollbacks, follow the corresponding release's lifecycle and encryption caveats.
