# School OS 5.3.9 — School Circle chat, compact notifications and mobile website

Cumulative update retaining earlier classroom, waiting-room, account wording and book-icon changes.

## Social chat

- No subject/topic field. Conversations are labelled with the other participants' names. A new message to the same one-to-one contact reuses the existing direct conversation.
- Search people by name, select removable recipient chips and load more results. The social-chat directory is filtered on the server and returns 20 results at a time, instead of sending an entire school list to the browser. Group size remains at most 30 recipients.
- Sent and received message bubbles, readable conversation headers and a phone view that keeps the open conversation and composer in view.

### Contact policy

| Account | Permitted direct contacts |
|---|---|
| Student | Students linked to the same current class, their own linked parent/guardian accounts and their assigned teachers |
| Teacher | Assigned learners and their linked guardians; school colleagues |
| Parent/guardian | Their linked children, those children's assigned teachers and school administrators |
| School administrator | School colleagues and parents/guardians; student updates use school/classroom announcements rather than private social chat |
| Non-teaching staff / Admissions | School colleagues, including teachers, staff, admissions and school administrators |

Cross-school contact is denied. Student-to-owner and student-to-non-teaching-staff social chat is denied in both directions. Groups must satisfy the policy for every pair of participants. The same checks run on creation, sending, fetching and opening older conversations. Older chats that no longer meet the policy are hidden/unavailable; their stored records are preserved. Unread chat notices exclude those blocked conversations. Search access alone does not grant message access.

Platform and partner support/referral workflows remain outside school social chat. Legacy structured Family Space requests retain their own forms; the topic-free redesign applies to School chat.

## One-way service notifications

Chat is separate from operational notices:

- Assigned drivers and transport managers can select an active assigned route and send a route update to its allocated learners and their linked guardians. A driver cannot target another driver's route or arbitrary students.
- Librarians can search issued loans by learner/book and send a fixed return reminder, including the book and due date. Returned/non-issued loans are not eligible for a new reminder. This opens no private learner chat.
- Existing communications/announcement permissions remain in place for staff assigned those responsibilities. No general student-messaging permission is granted to every staff member.

The service notification composer appears below School chat for eligible roles. It uses existing notification tables and is in-platform only; it does not purchase SMS/email delivery. Existing Operations/Library workspaces must be activated. Loan and route access are rechecked when sending, and duplicate submissions do not duplicate a notice.

## Compact notifications and automatic sound

Notifications start collapsed, with an unread count and **Show details**. **Hide details** makes them compact again; the choice is remembered separately for each account on that browser. Full notice text stays hidden while collapsed. The detailed inbox still supports marking notices read.

Sound is enabled by default. The Sound on/off and Pause rotation buttons are removed. Once the browser receives an initial click/tap/key interaction, unread notifications produce brief tones and a gentle reminder approximately every 30 seconds while the page is visible, including when details are collapsed. Marking notices read clears the unread reminder. Multiple tabs for the same account share a reminder timestamp to reduce overlapping tones. Confirmed-save tones remain.

Browsers/operating systems retain autoplay, volume and mute controls: software cannot silently bypass them. Each newly loaded page may need an interaction before audio can start. Automatic notice rotation respects the device's reduced-motion preference. Notifications continue to refresh by polling; they are not offline browser push.

## Phone website

The public site no longer shows a Pause motion button. The mobile homepage uses swipeable feature/start-step cards, a shorter hero/preview, an optional expandable discovery break and a reachable demo/start dock. Content remains available instead of being removed. Desktop discovery stays open, navigation/theme controls remain, and reduced-motion preferences are respected. Website dashboard preview images are refreshed to show the compact notification interface.

## Installation

1. Back up files, database and matching private keys. End active classes; test on staging.
2. Install **SchoolOS_5.3.9_Social_Chat_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.9** and refresh portal and website tabs. Existing accounts, messages, media settings and student records remain in place. No schema migration is required.
4. Test teacher/student/parent and driver/librarian accounts. Check permitted search, denied contacts, group rules, actual message receipt, route/loan notices, collapse persistence and sound after a tap. Verify real phone browsers as well as desktop.

## Validation and limits

Server tests cover the contact matrix, denied forged/cross-school recipients, mixed-group rejection, direct-chat reuse without a subject, scoped route/loan delivery and fixed library reminders. Browser tests cover name search/pagination, actual exchanged messages, hidden contacts, notification collapse persistence, default audio and repeat-tone generation, staff notice targeting and phone/desktop website layout. A synthetic directory verified contacts beyond the first page; those extra test accounts were removed. Role-page rendering and installer recovery/rollback checks were repeated.

Chat/notice data is school-scoped and stored in the existing database. No external messaging provider or new media service is provisioned.

See the [validation summary](SchoolOS_5.3.9_Validation.md) for the completed checks.

## Rollback

End classes, restore the updater's recorded 5.3.8 backup, then refresh pages. File rollback restores the earlier chat permissions and notification controls, so review the implications before reopening student chat. It does not undo sent messages/notices or restore database history. Restore a consistent protected database backup if reverting data is required; no schema change is introduced here.
