# School OS 5.3.16 validation

Local checks on 15 November 2026 (WAT) with an isolated fictional school and independent driver/parent browser sessions. No production data or authenticated live session was accessed.

## Daily bus and contact permissions

- Passed: Invalid first action rolls back automatic journey creation; unassigned pupils and drivers are denied
- Passed: Picked up starts and records today’s journey atomically; retries do not duplicate records or notices
- Passed: Not picked up requires a reason and pickup completion remains explicit before the home journey
- Passed: Daily home records preserve approved collector, identity and one-time-code checks
- Passed: The child’s bus record uses the same pupil-linked rows and rejects unrelated children
- Passed: Parent and assigned driver can find each other and exchange messages both ways
- Passed: Bus chat does not permit unrelated parents, private pupil chat or parent-to-parent group leakage
- Passed: Releasing the shared route immediately revokes contact, existing chat reads and sends
- Passed: Today’s driver dashboard includes charts and pupil actions; generic Tasks is absent from driver navigation
- Passed: Stale daily forms cannot write a new day’s bus record

## Retained transport guards

- Passed: Driver can report an assigned vehicle before the first trip; another driver cannot
- Passed: Expired licence, unavailable vehicle and insufficient capacity prevent dispatch
- Passed: Only assigned driver starts trip; fixed pupil list and duplicate/concurrent guards work
- Passed: Pickup boarding needs no guardian token; non-travel needs a reason and reaches linked family
- Passed: Completing a journey requires the destination and vehicle-clear confirmation
- Passed: Drop-off requires today’s approval, physical identity check and the school’s one-time token
- Passed: Location sharing is limited to own active, enabled trip and validates coordinates/accuracy
- Passed: Route updates reach only assigned pupils/guardians and retry without duplicate notices
- Passed: Driver reports and totals exclude other drivers and management permissions remain denied
- Passed: Older trip recovery rejects backdated boarding/GPS but permits reasoned closure
- Passed: Older on-board home journey requires coordinator review, with no invented handover
- Passed: Every driver view and default home render without PHP warnings or teaching/finance widgets

## Browser and live integration

- Passed: Driver home includes charts and daily pupil controls; Tasks menu is removed and old link redirects
- Passed: Picked up saves in place and appears on the parent’s bus page without reload
- Passed: Not picked up records a reason; polling preserves drafts and pickup closes on explicit confirmation
- Passed: Home bus and verified drop-off update the same child record and parent view in place
- Passed: Chat parent and Chat driver open the same conversation and messages arrive both ways
- Passed: Transport APIs reject unrelated child access and missing security tokens
- Passed: Home charts and daily pupil list fit 1440, 390 and 320px in both themes
- Passed: A pupil action during a delayed live refresh queues and saves without another click

## Installer and recovery

- Passed: Existing 5.3.15 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.16 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.15 metadata
- Passed: Traversal entries are refused before file changes

631 role-page visits across 14 synthetic roles returned without HTTP/PHP rendering errors. Changed PHP and JavaScript syntax passed. Driver home was checked at 1440, 390 and 320 pixels in light and dark themes. Browser integration observed pickup and verified drop-off on the already-open parent page without reloading it, and exchanged actual local chat messages in both directions.

A delayed-refresh test held a daily GET for 1.5 seconds, submitted a pupil action during that refresh, and confirmed the queued write saved without a second click. Draft input survived a live polling cycle. API requests without a security token and requests for an unrelated child were refused. Automatic journey creation and the first pupil outcome roll back together if validation fails. Existing recorded outcomes are acknowledged without duplicate rows or notifications.

Private-contact checks cover both allowed directions, unrelated parents, student chat exclusion, parent-group isolation, assignment revocation and current thread checks. The change does not give all staff broad access to families.

The release manifest hashes every shipped file. Configuration, database data, synthetic credentials and local test scripts are excluded from the ZIP. Installer validation covers failure recovery, committed deployment with matching hashes, duplicate-version refusal, file rollback and traversal rejection. Screenshots are fictional examples published separately from the installable package.

Live updates use ordinary polling and were tested locally; the production host has not been load-tested and no production update has been installed by these tests.
