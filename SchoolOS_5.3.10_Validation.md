# School OS 5.3.10 validation

Local integration validation on 14 November 2026 with synthetic school accounts and chat messages.

## Server

- Passed: Typing identifies another participant but never includes draft text
- Passed: Explicit stop, send and stale heartbeat all clear typing
- Passed: Participants can add, aggregate, replace and remove their own reactions
- Passed: Emoji variants, flags, skin tones, keycaps and family sequences are accepted; text and multiple emoji are rejected
- Passed: Outsiders and forged message references cannot read typing or change reactions
- Passed: Reaction snapshots exclude references to messages outside the permitted thread

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

## Group

- Passed: Multiple group participants are identified separately, excluding the viewer

## Narrow

- Passed: compose at 320×568
- Passed: reaction at 320×568
- Passed: compose at 390×844
- Passed: reaction at 390×844
- Passed: compose at 740×360
- Passed: reaction at 740×360

## Updater

- Passed: Existing 5.3.9 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.10 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.9 metadata
- Passed: Traversal entries are refused before file changes

593 role-page requests passed without HTTP/PHP rendering failures. Changed PHP/JavaScript syntax and final package hashes were verified.

The browser scenarios used independent teacher/student sessions, actual API delivery and persisted database state. Device emoji appearance, real school network latency and mobile browser keyboard behavior still require acceptance checks.
