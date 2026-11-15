# School OS 5.3.15 — driver workspace

## What changed

Drivers now land in a dedicated **Driver workspace** on sign-in and from their operations menu. The generic staff dashboard's teaching/timetable widget and empty operations landing are removed for driver accounts without transport-management access. Personal staff attendance, school announcements, tasks and colleague chat remain available through their existing permissions.

The workspace uses the same glass surfaces and readable light/dark theme system as the updated HR portal, with clear navigation and labelled charts. Driver controls use route, vehicle, stop and pupil names instead of database IDs.

[Light theme preview](SchoolOS_5.3.15_Driver_Light.png) · [Dark theme preview](SchoolOS_5.3.15_Driver_Dark.png)

## Driver menus

| Menu | Purpose |
| --- | --- |
| My day | Assigned routes, licence information, today's journey totals and the current open trip. Named start buttons open the pupil list directly. |
| Routes & pupils | Only the active driver's assigned routes, vehicles, ordered stops and allocated pupils. Shows current assignments, not other drivers' work. |
| Trip history | Own past journeys, date filtering and 20-trip pages; each opens its recorded pupil list. |
| Reports | Date-filtered pupil-journey outcome donut/pie, seven-day journey completion chart and the selected day's trips. No teaching or school finance widgets. |
| Route updates | One-way in-platform notices to assigned pupils and their linked guardians, with recent sent-notice history. Sending stays in the driver workspace. |
| Vehicle care | Report an assigned vehicle before a trip, or attach a problem/incident to an owned journey. See own reports and whether the coordinator has closed them. |

The driver cannot manage the fleet, renew licences, assign routes/pupils, set fees, approve guardian requests or close coordinator reports. Those actions remain restricted to transport managers/school administrators on the server. Report totals are scoped to the driver who recorded the trip; current route reassignment does not expose another driver's history.

## Daily journey workflow

1. **My day** shows a priority card when a journey is already open. Finish or reconcile its records before starting another trip.
2. Start **School pickup** or **Home drop-off** from an assigned route. A valid active driver/licence, active vehicle, pupil assignments and enough seats are required. Duplicate daily journeys and overlapping active vehicle/driver use remain blocked.
3. The trip captures a fixed pupil list. Later route assignment changes do not rewrite it. Search by pupil or stop and expand the relevant pupil card.
4. For school pickup, confirm the pupil is on board, or record **Not travelling** with a reason. A guardian pickup token is not required for boarding or non-travel.
5. For home drop-off, record boarding first. Then hand over only to a collector approved for that pupil and journey date, after physical identity verification and a meaningful handover note. If the school requires a one-time pickup code, it is required only at handover and is consumed once. Once on board for a home journey, a pupil cannot simply be relabelled as not travelling.
6. A home journey cannot finish while pupils remain pending or on board awaiting handover. Completion also requires confirmation that the driver has reached the destination, checked pupil outcomes and checked the vehicle is clear. Coordinators use the same completion confirmation.
7. Pupil state changes create linked-family in-platform updates. Boarding and home handover have separate notification keys, so a handover does not disappear behind an earlier boarding notice. These actions do not send external SMS or WhatsApp.

Save/finish actions retain the open journey context. Buttons disable during valid form submission to reduce repeated taps; server checks still enforce state and permissions independently.

## Older unresolved journeys

An older trip is clearly identified. Drivers cannot record a fresh boarding or GPS update against a past service date. A genuinely non-travelling pending pupil can be recorded with a reason so the older record can be closed. If a home passenger remains recorded on board across the day boundary, the driver cannot bypass identity/approval rules or mark them absent to finish.

For an older open trip, the transport coordinator has an **exception review** form on the existing management trip page. It requires verified pupil whereabouts and supporting explanation. The pupil receives a distinct **Coordinator reviewed** outcome and a retained incident/audit record; this does not invent or authorise a guardian handover. Linked guardians receive a notice of the review. Drivers cannot perform this review. The trip can then be completed after its remaining records and vehicle-clear check are resolved.

## Connected features and limits

- **Route updates:** use existing route assignments and verified parent/student links. A stored notice is not proof it has been read. Sending the same notice nonce again does not create duplicate notifications. The sent history shows up to 100 recent sends.
- **Guardian handovers:** use the existing parent authorisation and school approval workflow. A token/QR code alone does not replace the physical identity check. The driver enters the one-time code when required; no new camera-based QR scanner is added.
- **GPS:** optional and enabled per route by the coordinator. A deliberate button reads the device location, then a separate submission shares it. Requires HTTPS, permission and an active trip dated today. Stores the latest point, not a continuous background track or a live navigation map. Coordinates remain restricted to authorised transport staff. This is device-reported data, not independently verified vehicle tracking.
- **Vehicle reports:** work before the first journey for a currently assigned vehicle. A report does not itself put a vehicle into maintenance or close it; the coordinator manages fleet status and review.
- **Reports:** count recorded trips and pupil-trip outcomes, not unique pupils, punctuality, speed, distance, driving quality or attendance/payroll performance. Pickup boarding remains a historical boarding entry after the journey finishes. The donut includes coordinator-reviewed exceptions separately. Each trip list page contains up to 20 trips; selected-date report cards show up to 20 and further entries can be opened from history.
- **Scheduling:** the assigned route's time window is informative. This update does not create automatic dispatch, road routing or separate morning/afternoon timetable planning.
- **Chat:** retains existing colleague/student privacy rules. Route notices do not grant drivers private chat access to pupils or every parent.

## Installation

1. Back up the application and database and test the update on staging. Finish active journeys before replacing files.
2. Install **SchoolOS_5.3.15_Driver_Workspace_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.15**, then refresh driver, coordinator and parent dashboard tabs.
4. Check a driver's account is linked to an active driver profile with a valid licence, assigned vehicle, route, stops and pupils. Existing accounts and assignments are retained; missing setup is explained in the workspace.
5. Test a school pickup and home handover with linked test accounts, then check parent notifications and a pre-trip vehicle report. Check both phone and desktop layouts.

This cumulative package retains previous HR, chat, classroom, notification and mobile improvements. No schema migration, external provider or new subscription is required. Existing transport records use their original tables; the additional coordinator-reviewed exception is a new named outcome in the existing status field.

## Rollback

The updater supports file rollback and preserves configuration. File rollback does not erase pupil records, messages or reviews made after installation. **Complete/reconcile open home journeys before rolling back**: the older version does not support the new home-boarding transition or coordinator-reviewed exception UI. Retain the database backup if business-data restoration is required; do not silently discard later handover or notification records.

[Driver audit and validation](SchoolOS_5.3.15_Driver_Audit.md)
