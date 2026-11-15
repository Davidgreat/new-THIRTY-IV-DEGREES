# School OS 5.3.15 — driver audit and validation

Reviewed current source and synthetic local school accounts on 15 November 2026 (WAT). The Companion Page provided no readable authenticated document; no production driver account, pupil data or hosting configuration was accessed or changed.

## Findings and changes

| Finding | Resolution |
| --- | --- |
| Driver home could fall through to generic staff/teaching widgets | Driver-specific default workspace and operational navigation |
| Two broad transport tabs mixed start forms with up to 100 full trip manifests | My day, assigned routes, paged history, focused pupil list, reports, updates and vehicle care |
| Incident reporting required an already-created trip | Current assigned vehicle can be reported before departure; server still checks assignment |
| Route notices were hidden in chat and redirected there | Dedicated route-update screen reuses scoped notification engine and preserves driver context |
| School pickup-code setting could add a required code field to ordinary boarding | Code input and enforcement are confined to guardian handover |
| Home trip could omit a distinct boarding stage | Driver UI/server support boarding then approved handover; completion blocks on-board home passengers |
| One notification key per pupil/trip would hide a subsequent handover after boarding | Separate state-specific notifications, protected against duplicate state submissions |
| Starting driver permission was checked before route/vehicle/driver locks | Locked driver ownership is checked again before dispatch |
| Past trips could receive fresh boarding or location updates | Journey-date checks, explicit older-trip guidance and coordinator-only exception review |
| Coordinator recovery could be confused with verified guardian collection | Distinct reviewed-exception state, evidence, audit and linked-family notification; no invented handover |
| Completion had no destination/vehicle-clear acknowledgement | Required confirmation for drivers and coordinators |
| Saving from workspace or trip could return to a generic operations page | Transport-specific redirects and automatic opening of the started trip |
| Reports/labels exposed technical IDs or irrelevant academic widgets | Named controls, driver-scoped charts, real outcome labels and current assignment information |

## Relevant permissions and connections

Driver work is restricted by school, active assigned driver profile or recorded trip owner. Fleet, licence, route/student allocation, fee and report-review actions stay with authorised management. Own employment remains personal self-service; it does not grant HR management. Pupil manifests and route lists omit schoolwide pupil data, fee amounts and other drivers' reports. Parent notices use verified pupil-family links. Approved collector checks, one-time codes where enabled and physical verification remain required. Optional GPS remains foreground/latest-point reporting.

## Automated local checks

### Server integration and privacy

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

### Browser workflows and responsive themes

- Passed: Default login opens the driver workspace with relevant menus
- Passed: GPS reads only after a deliberate click and saves on the active journey
- Passed: Pupil outcome and checked-vehicle completion save without leaving the journey
- Passed: Route notice stays in driver workspace and reaches linked parent notifications
- Passed: Assigned vehicle report saves with coordinator-review status
- Passed: All six driver views fit light/dark screens at 1440, 390 and 320px; charts render real journey data

### Installer and recovery

- Passed: Existing 5.3.14 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.15 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.14 metadata
- Passed: Traversal entries are refused before file changes

631 role-page visits across 14 synthetic roles passed without HTTP/PHP rendering errors. Changed PHP and JavaScript syntax passed. Browser tests used independent driver and parent sessions and a device-location simulation. All six workspace pages were checked at 1440, 390 and 320 pixels in both light and dark themes.

The isolated transport test school and fictional users were removed after validation. Configuration, passwords, uploaded/private data and local tests are excluded from the installable ZIP. Every shipped file is hashed in the release manifest, and installer tests cover injected-failure recovery, committed deployment, duplicate-version refusal, explicit rollback and traversal rejection.

These checks validate the local build and integrations; they are not a production road test, background GPS service, vehicle-tracking guarantee or legal/safeguarding certification. The deployment guide records the actual workflow and remaining limits, including rollback implications for new passenger states.
