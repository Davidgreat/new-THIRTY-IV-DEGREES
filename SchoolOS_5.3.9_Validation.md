# School OS 5.3.9 validation

Local integration validation on 14 November 2026 with synthetic school accounts, routes, loans and messages.

## Policy

- Passed: Students can chat with classmates, linked parents and assigned teachers, but not owner or service staff
- Passed: Staff colleagues can chat; cross-school people cannot be addressed
- Passed: Search returns bounded results and filters unauthorized names on the server
- Passed: Forged recipients are rejected and no subject is needed for a normal direct conversation
- Passed: Mixed groups cannot bypass student-to-staff restrictions
- Passed: A service role cannot forge another service or school notice target
- Passed: Assigned route notice reaches only its allocated learner accounts and guardians
- Passed: Issued-loan reminder is scoped to its learner and contains a fixed return message

## Ui

- Passed: Chat has no subject and displays a bounded searchable people picker
- Passed: A later-page name is searchable and owner/staff are absent for a student
- Passed: Notifications are compact by default and expand/collapse without old controls
- Passed: Sound defaults on despite an old off preference and repeats a brief unread reminder
- Passed: A social direct chat starts without a topic and delivers the actual message
- Passed: Notification collapse persists on another page and phone chat fits the viewport
- Passed: Service staff cannot find students in chat but can choose an assigned route notice
- Passed: Mobile homepage offers swipeable sections, optional discovery and clear start links
- Passed: Desktop website keeps the discovery section available and has no pause button

## Narrow

- Passed: 320px ?s=chat
- Passed: 320px ?home=1

## Visual

- Passed: Login page uses book mark
- Passed: schooladmin dashboard has no sparkle glyph
- Passed: Login page uses book mark
- Passed: parent dashboard has no sparkle glyph
- Passed: Login page uses book mark
- Passed: teacher dashboard has no sparkle glyph
- Passed: Teacher classroom uses book mark
- Passed: Login page uses book mark
- Passed: student dashboard has no sparkle glyph
- Passed: Waiting prompt uses book mark
- Passed: Phone waiting room still fits at normal zoom
- Passed: Public website uses book marks
- Passed: owner refreshed preview loads
- Passed: onboarding refreshed preview loads
- Passed: parent refreshed preview loads

## Updater

- Passed: Existing 5.3.8 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.9 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.8 metadata
- Passed: Traversal entries are refused before file changes

591 role-page requests passed without HTTP/PHP rendering failures. Changed PHP/JavaScript syntax was checked.

Audio tests observed actual Web Audio oscillator playback after a browser interaction, including the repeated unread reminder. Actual school phones, speaker settings and browser autoplay policies still need acceptance checks. The website was measured at 390px and 320px without horizontal overflow, and the refreshed preview images were captured from fictional records.

No external messaging account, billable delivery service or production database was used.
