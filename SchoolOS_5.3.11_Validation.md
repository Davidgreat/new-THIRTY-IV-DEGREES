# School OS 5.3.11 validation

Local integration checks on 14 November 2026 with independent synthetic teacher/student browser sessions.

## Server

- Passed: Typing identifies another participant but never includes draft text
- Passed: Explicit stop, send and stale heartbeat all clear typing
- Passed: Participants can add, aggregate, replace and remove their own reactions
- Passed: Emoji variants, flags, skin tones, keycaps and family sequences are accepted; text and multiple emoji are rejected
- Passed: Outsiders and forged message references cannot read typing or change reactions
- Passed: Reaction snapshots exclude references to messages outside the permitted thread

## Reliability

- Passed: A brief draft survives keyboard blur and 3.5 seconds of receiver delay
- Passed: Failed typing updates retry without another keystroke and show connection feedback
- Passed: Typing appears in the recipient chat list without opening or reading the conversation
- Passed: A paused draft eventually stops advertising typing

## Browser

- Passed: Typing reaches the receiver without disclosing the draft
- Passed: Typing disappears when the sender pauses or leaves the input
- Passed: The emoji picker inserts at the cursor and sends actual Unicode emoji
- Passed: A recipient can react to a message and the sender sees the reaction
- Passed: Matching reactions aggregate and each account can remove only its own
- Passed: Any valid single emoji can be used, including skin-tone and family sequences
- Passed: Reactions persist through reload and emoji messages remain intact
- Passed: Phone emoji menus and reaction controls fit without horizontal overflow
- Passed: Navigating away stops typing without leaving a stale indicator

## List Privacy

- Passed: A nonmember cannot see typing even when the sender is an allowed colleague
- Passed: Cross-school presence requests reveal no participants
- Passed: Authorized presence is visible and does not mark messages read

## Updater

- Passed: Existing 5.3.10 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.11 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.10 metadata
- Passed: Traversal entries are refused before file changes

595 role-page requests passed without HTTP/PHP rendering failures. Changed PHP/JavaScript syntax was checked.

The reliability scenario deliberately delayed receiver fetches by 3.5 seconds and aborted the first two positive sender typing requests. The updated client still delivered the indicator, retried without another input event and cleared it on idle. A separate scenario verified chat-list activity without changing last_read. These are local browser simulations; actual production devices/networks need acceptance testing.
