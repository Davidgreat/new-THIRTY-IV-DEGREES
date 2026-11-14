# School OS 5.3.14 validation

Local validation on 14 November 2026 with synthetic school records. No production data or hosting scheduler was accessed.

## Automatic day-close

- Passed: Midnight closes yesterday with absence, preserves presence/excused/leave and includes unlinked staff
- Passed: Current day remains pending; rerunning close is idempotent
- Passed: Quiet days catch up once and records remain tenant-scoped
- Passed: Manual correction supports staff without a login and retains correction history
- Passed: A missing clock-in is recorded absent only after its WAT day ends
- Passed: Leave approved after day-close replaces only automatic absences

## HR privacy and workflows

- Passed: Missing clock-ins, verified absence, leave and unlinked staff remain distinct
- Passed: HR can correct attendance with a reason without losing clock times
- Passed: Non-HR actors, cross-school records, future dates and dates before appointment are rejected
- Passed: HR issues a private query and only the linked staff member may respond
- Passed: Query notifications are scoped to staff and authorised HR
- Passed: Only HR closes a query with an outcome; closed records cannot be edited
- Passed: Staff profile includes history and pay but hides unpublished appraisals from the staff member
- Passed: New overview, date log, staff profile and query views render without warnings

## Browser workflows

- Passed: HR overview charts and date filtering
- Passed: Register opens a complete linked staff profile
- Passed: Profile chat opens the correct permitted staff conversation
- Passed: HR issue → staff response → HR outcome, with profile and self-service context preserved
- Passed: Overview, date log and full staff profile fit 320px and 390px screens

## Theme, layout and search

- Passed: Light/dark layouts and More tools fit 1440, 1024, 390 and 320px; text tokens exceed 4.5:1 contrast
- Passed: Daily register search filters names without changing chart totals

## Installer and recovery

- Passed: Existing 5.3.13 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.14 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.13 metadata
- Passed: Traversal entries are refused before file changes

625 role-page requests across 14 synthetic roles passed without HTTP/PHP rendering errors. Changed PHP and JavaScript syntax passed. The attendance-only all-schools CLI command executed successfully without running delivery jobs. Theme checks compare explicit primary/muted text tokens with the intended solid surface and verify ratios of at least 4.5:1; translucent backgrounds and other legacy pages have not received a complete accessibility certification. Browser tests verify charts, register search, More tools, Escape dismissal, staff chat, query response/outcome and narrow-screen overflow.

Day-close tests use an isolated synthetic school and controlled WAT date boundaries. They verify automatic absence, protection of recorded/approved/excused attendance, unlinked staff, induction/future-start exclusion, repeat safety, quiet-day catch-up, manual correction history and retrospective leave approval. These are boundary simulations, not a claim that a production cron job was configured or observed overnight.

The package manifest hashes every shipped file. Configuration, secrets, database data, screenshots and test fixtures are excluded from the installable ZIP. The published ZIP is also verified after download. Existing file rollback restores version 5.3.13; attendance business records are intentionally not erased by file rollback.
