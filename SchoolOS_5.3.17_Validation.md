# School OS 5.3.17 validation

Local checks on 15 November 2026 (WAT), using an isolated fictional school and independent browser accounts. No production school data or authenticated live session was accessed.

The previous bug was reproduced before the change: recording home absence after a pickup returned “Driver or vehicle already has an active trip.” The updated test repeats that situation without closing pickup first.

## Server integration and role eligibility

- Passed: Home non-travel saves while school pickup is open, without dispatching a second bus trip
- Passed: Non-travel retries stay idempotent and a plan cannot bypass active-trip or GPS restrictions
- Passed: Home boarding activates the same plan after pickup closes and preserves saved non-travel
- Passed: Drop-off is discoverable before boarding; collector approval is still required after boarding
- Passed: Driver, warden, HR, librarian, store, communications, admissions, teacher and employed owner can clock in/out
- Passed: Every employee role has a shared attendance widget; family/student accounts do not
- Passed: Unlinked, onboarding and future staff are guided rather than silently clocked; stale-day forms are refused
- Passed: Exiting staff may record attendance; users cannot clock out before clocking in
- Passed: Admissions has a linked self-employment view without HR management authority

## Browser workflows and employee dashboards

- Passed: Driver clocks in and out from the dashboard attendance bar without navigation
- Passed: Not travelling home saves during the still-open pickup and reaches the parent bus record
- Passed: Blocked home boarding gives an inline explanation beside the pupil action
- Passed: Home plan activates after pickup closes; Drop off is explained, approval-gated and saves a verified handover
- Passed: Teacher, HR, warden, librarian, store, communications, Admissions and employed owner clock in/out on their own dashboards
- Passed: Parent does not receive staff attendance controls or staff API access
- Passed: Staff attendance, history and driver cards fit 1440/390/320px in both themes
- Passed: Clock-in during a delayed attendance refresh queues and saves without another click

## Installer and recovery

- Passed: Existing 5.3.16 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.17 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.16 metadata
- Passed: Traversal entries are refused before file changes

643 role-page requests across 14 synthetic account types passed without HTTP/PHP rendering errors. Changed PHP and JavaScript syntax passed. Staff and transport controls were checked at 1440, 390 and 320px in both light and dark themes. Employee browser checks performed real local clock-in and clock-out requests for the listed roles; they did not merely check button visibility. Parent pages were observed updating without reload after non-travel and verified handover. A delayed attendance GET also confirmed that a simultaneous clock-in request is queued and saved without another click.

New home plans are not counted as active trips. Actual activation reuses the same trip/passenger snapshot, retains saved non-travel choices and runs dispatch checks. Collector, identity and one-time token checks remain in force. Staff endpoint access remains restricted to employee roles and current authenticated identity; family accounts receive no attendance controls and are refused staff API access.

The package manifest hashes every shipped file. Configuration, database data, synthetic credentials and local tests are excluded from the installable ZIP. Installer checks cover injected failure recovery, full hash-matched deployment, duplicate-version refusal, file rollback and path-traversal rejection. The attendance screenshot is a fictional preview supplied separately.

Production hosting and staff devices have not been load-tested or modified by these local checks. Eligibility, calendar-day attendance limits and planned-state rollback implications are documented in the guide.
