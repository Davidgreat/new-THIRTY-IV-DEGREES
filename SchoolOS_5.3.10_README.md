# School OS 5.3.10 — typing, emojis and message reactions

Adds live interaction to **School Circle chat**, while retaining the existing school/contact/group permissions and earlier portal updates.

## Typing indicators

When another participant types in an open conversation, you see their name and **is typing…**. Group chats identify the people currently typing. Your own typing is not shown back to you.

Only a short presence signal is sent: draft text is never transmitted. The signal stops when the input is cleared, a message is sent, focus leaves the input, the tab becomes hidden or the page is left. Stale signals expire after roughly six seconds if a browser closes or loses connectivity unexpectedly. The visible chat refreshes about every two seconds, so this is near-real-time polling rather than a dedicated WebSocket connection. Background/offline browser behavior can delay updates.

## Emoji messages

Select the smile button beside the message box, choose a quick emoji, then send normally. Emojis are inserted at the cursor, and can be mixed with text. Your phone/desktop keyboard can supply other emojis. Escape, the smile button or a click outside dismisses the picker. Emoji appearance follows the device's installed emoji fonts.

## Message reactions

Select **React** on a message. Choose a quick emoji, or paste a single emoji under **Any other emoji** and select **Use**. Flags, skin tones, keycaps and family/joined sequences are supported when represented as a valid single emoji.

- Each participant has one reaction per message. Choosing a different emoji replaces their own reaction.
- Matching reactions show a count. Your selection is highlighted; desktop tooltips show the current participants' names.
- Select your highlighted reaction again to remove it. You cannot remove another person's reaction.
- Reactions persist after reload and update for other participants while they view the conversation.

Typing and reaction endpoints recheck membership and the current contact policy. Outsiders, forbidden student/staff relationships, cross-school accounts and forged message references cannot use them. Reactions do not create a new private contact or add anyone to a conversation.

## Install

1. Back up files, database and matching private keys. End active classes and test on staging.
2. Install **SchoolOS_5.3.10_Chat_Typing_Reactions_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.10** and refresh the chat tabs for all participants. Existing messages, accounts, privacy settings and central media configuration remain in place.
4. Open the same permitted conversation in two accounts. Type, pause, send an emoji message, add/change/remove reactions and reload. Verify a phone as well as desktop.

No schema migration or external messaging service is required. Typing timestamps use the existing account-progress store; reactions use the existing configuration store with school/message-scoped keys. No new recording, camera or microphone request is added by chat.

## Validation

Server tests cover typing privacy, stop/send/expiry, reaction ownership/counting/replacement/removal, complex Unicode emoji, invalid-input rejection and forged/outsider message access. Group presence identifies multiple participants separately. Two-account browser tests cover actual typing delivery, emoji message receipt, live reaction counts, custom family emoji, persistence, navigation cleanup and phone menus. Narrow phone and landscape layouts, role-page rendering, syntax, package hashes and installer failure recovery/rollback were checked.

See the [validation summary](SchoolOS_5.3.10_Validation.md) for completed checks. Existing notification/browser sound rules from 5.3.9 still apply; reaction updates themselves are shown inside the conversation.

## Rollback

End active classes, restore the updater's recorded 5.3.9 backup and reload pages. Emoji message text remains readable. Stored reactions are retained but the older interface does not display them; old typing timestamps are ignored. This update adds no schema changes. Follow the matching guides if rolling back earlier releases with different chat/contact rules.
