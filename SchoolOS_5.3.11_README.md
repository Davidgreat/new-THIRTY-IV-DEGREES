# School OS 5.3.11 — typing indicator reliability

Fixes missed typing updates and adds activity previews to the chat list, while retaining emoji messages, reactions and existing contact permissions.

## What was corrected

The previous sender could clear its typing flag immediately when an input lost focus, or after a short pause, before the receiver's next refresh. A short draft plus keyboard blur and a delayed receiver reproduced a missed indicator locally. Failed typing requests were also silently dropped until another input event.

- A short activity window now survives keyboard blur and brief pauses. Idle typing stops about 5.5 seconds after the last input. Sending, clearing the draft or leaving the page still clears the signal; abandoned signals expire after about ten seconds.
- Active typing updates are throttled, serialized and retried after a failed request without requiring another keystroke. Repeated failures show a small **Typing update couldn’t connect. Retrying…** message to the sender rather than failing silently.
- The open conversation refreshes about every 1.5 seconds. Typing presence is returned as explicit numeric lifetimes.
- Visible chat-list rows also show **Typing…**, so the receiver can see activity before opening the conversation. Reading presence does not mark messages as read.

No draft text is sent. Group/contact checks remain enforced. A nonmember or another school cannot see typing. Device/browser throttling and real network availability still affect timing; this is near-real-time polling, not a new WebSocket service.

## Install and test

1. Back up files, database and private keys, end active classes and test on staging.
2. Install **SchoolOS_5.3.11_Typing_Reliability_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.11**, then **refresh the chat page on both the sender's and receiver's devices/browsers**. Close and reopen old tabs if necessary. Old loaded pages cannot show features from a newly installed script until refreshed.
4. Open a permitted conversation on both sides, type a short reply and pause. The receiver should see the sender's name and typing indicator. Repeat while the receiver is viewing the chat list instead of the open conversation.
5. If the sender shows the connection-feedback message, note that message and verify that both pages are refreshed and signed in. Message sending remains separate from typing presence.

Existing messages, reactions, accounts and saved media settings remain in place. No database schema migration or provider configuration is required. No draft persistence or new private contact permission is added.

## Validation

The delayed-receiver/blur reproduction now shows the indicator. Browser tests also passed for retrying two deliberately failed updates without another keystroke, sender connection feedback, chat-list typing without read-receipt changes, idle expiry and the existing nine emoji/reaction/typing workflows. Server tests cover scope, membership, Unicode reactions, expiry and read-receipt isolation. Role-page rendering, changed syntax, package hashes and installer recovery/rollback were checked.

See the [validation summary](SchoolOS_5.3.11_Validation.md). Actual school devices/networks should be checked after installation; no production account was used for the local tests.

## Rollback

End active classes, restore the updater's recorded 5.3.10 backup and refresh both sides' chat tabs. The earlier typing timing and absence of list activity will return. Stored emoji messages/reactions remain; this release adds no schema changes.
