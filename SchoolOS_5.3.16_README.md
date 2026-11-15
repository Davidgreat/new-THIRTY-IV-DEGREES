# School OS 5.3.16 — daily pupil bus records and parent–driver chat

## Why the earlier screen was confusing

The screenshot showed **My Tasks**, the generic personal to-do list. It does not record a pickup, drop-off or school bus journey. The previous driver update also left the charts under Reports rather than on the main landing page.

This release removes Tasks from the standard driver menu and redirects an old driver `?s=tasks` bookmark to the dashboard. Existing task data is retained; the task feature remains available to other account types. The driver walkthrough is now specific to the bus workflow and opens on request instead of automatically covering the dashboard.

**Driver dashboard** now contains the glass interface, pupil totals, donut/pie chart, seven-day chart, open-journey controls and **Today’s pupils**. The top **Today’s pupils** shortcut jumps straight to the daily list. The visible **School bus workspace · 5.3.16** badge helps identify the installed build.

[Light dashboard](SchoolOS_5.3.16_Driver_Home_Light.png) · [Dark dashboard](SchoolOS_5.3.16_Driver_Home_Dark.png)

## Daily pickup and drop-off

1. Open **Driver dashboard**, find the pupil by name/route/stop and expand their card.
2. In School pickup, select **Picked up**, or **Not picked up** with a reason. Common reasons are selectable; Other requires a short explanation.
3. The first valid action opens today's dated journey record when necessary and saves the pupil outcome in the same transaction. A failed first action leaves no empty journey behind. Repeating an already-saved outcome does not duplicate the record or notification.
4. After all pickup outcomes are recorded, confirm the destination/pupil/vehicle checks and **Finish school pickup**. The school bus cannot start a conflicting home or other route journey while an earlier journey is open.
5. For the return trip, select **On home bus** or record **Not travelling home**. Once on board, **Drop off** opens the approved collector controls. Confirm the approved collector, physical identity check and handover note; enter the one-time guardian code if required by the school.
6. Complete the home journey after all outcomes and the vehicle-clear confirmation. Older open journeys remain visible and must be reconciled; existing coordinator-only exception review is retained.

The daily screen saves in place. It queues a save made during a live refresh instead of discarding the click. Unsaved reason/collector fields, open pupil cards and nested panels are preserved while updates arrive. A form left open across the WAT day boundary cannot silently write against the next day.

## Stored against the pupil’s school bus record

Daily actions use the existing `tm_trips` and `tm_passengers` records, linked by the pupil's `student_id`, route, journey direction and service date. This is the same source read by the school’s transport management, the driver reports and the child’s transport history. No separate manual copy into a pupil database is needed and no duplicate bus-status column is created.

Parents see **School bus record** under the linked child’s transport page, with dates, pickup/home direction, state, route and recording time. The latest 40 pupil-journey entries are displayed; older records remain stored and available to school transport management. A bus non-travel record does **not** mark the child absent from academic lessons or change payroll—families may use another means of transport.

## Two-way parent–driver chat

- A driver expands a pupil card and uses **Chat parent** to open the permitted linked guardian conversation.
- A parent opens the child's transport page and uses **Chat with driver**.
- If the conversation already exists, both buttons open that same conversation. Otherwise, the first message starts a private conversation in the existing chat system. The searchable contact picker also identifies **Assigned school bus driver** and **Parent on your bus route**.
- Both directions require a verified parent-child link, active bus assignment, active route/driver profile, active accounts and driver access. Merely being school staff does not grant access to every parent. Drivers do not gain private pupil chat through this change.
- Removing/releasing the shared assignment or disabling the relevant relationship revokes contact and existing-thread read/send access. Stored messages are retained. Parent-to-parent group exposure is not introduced.

Route announcements remain available separately for one-way allocated-family notices. Existing typing, emoji and message reactions continue through the same chat system.

## Live behaviour

The driver's successful save updates their page immediately after the server confirms it. Open driver/child transport pages check for new records approximately every **8 seconds** and retry after connection errors; returning to a visible tab requests an update. Chat retains its existing approximately 1.5-second refresh. This is near-real-time polling on the existing PHP application, not a new WebSocket or paid messaging service. Background browser throttling, network delay and closed pages affect update timing.

Transport endpoints enforce the current account, school/child ownership, operation permissions, request method and security token. They do not rely on the menu to enforce access. No new external SMS, WhatsApp or push service is configured.

## Installation and confirmation

1. Back up the application and database, and test on staging. Finish/reconcile open journeys before replacing files.
2. Install **SchoolOS_5.3.16_Driver_Daily_Transport_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm version **5.3.16**. Refresh driver and parent tabs, then open **Driver dashboard**.
4. Confirm the **School bus workspace · 5.3.16** badge, the pie/seven-day charts and Today’s pupils. My Tasks should no longer appear in the normal driver menu; an old Tasks link should redirect here.
5. If that badge is missing, the page is still using an older build/tab. Check the installed update version and refresh before testing the new workflow.
6. Test one linked pupil with a driver and parent account in separate browsers: record pickup, observe the child’s bus page, and exchange a message both ways. Continue through the verified home handover with test records.

Existing driver profiles, routes, pupils, accounts, messages and history are retained. No schema migration, new provider or cron setup is required for the new daily screen/chat. The package is cumulative and preserves previous HR, classroom, notification, vehicle-care and transport safeguards. The installer invalidates replaced PHP files where supported and uses new CSS/JavaScript asset version URLs.

## Retained limits and rollback

A valid assigned driver/licence, suitable active vehicle and pupil assignments are still required to start a journey. A pupil already on a home journey cannot be marked as non-travelling to bypass guardian verification. A pupil already in an opened journey remains in that snapshot even if assignments subsequently change; chat follows current active family/route permissions.

GPS remains optional foreground/latest-point reporting, not background vehicle tracking. Reports count records, not verified speed, distance or punctuality. Academic attendance and payroll remain separate. After a long offline period, refresh the dashboard before recording a new day.

File rollback retains entered business data. Finish/reconcile active home journeys before rolling back; the older interfaces do not provide the same daily controls or bus-chat permissions. Reverting this release removes the new parent–driver contact permission, so those conversations may become inaccessible while the messages remain stored. Keep the database backup if business-data restoration is required; do not discard later handover records silently.

[Validation report](SchoolOS_5.3.16_Validation.md)
