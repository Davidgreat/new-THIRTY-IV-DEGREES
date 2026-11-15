# School OS 5.3.17 — home travel choices and staff attendance

## Fixed: Not travelling home while pickup is open

The reported failure was reproduced: after recording a school pickup, the previous version attempted to start a second live journey when saving **Not travelling home**. The active pickup guard rejected that request, and its feedback was easy to miss above the pupil list.

A home non-travel decision now saves as a dated **home plan**, without dispatching a second bus trip. The morning pickup stays open and its remaining pupils can still be recorded. Parents see the saved home non-travel record in their child's bus history and existing in-platform updates.

When the driver later starts home boarding, that same plan becomes the active home journey after normal driver, vehicle, licence, capacity and conflicting-trip checks. Previously saved non-travel outcomes remain intact. Plans are separately labelled **Home plan · not started**, with a separate colour in journey charts. They are records of planned travel choices, not proof a vehicle departed or travelled a route.

Validation failures now appear beside the pupil's action as well as in the dashboard status area. Saving a non-travel choice still requires selecting a reason and pressing **Save**; expanding its panel alone does not record an outcome. Repeated saves do not create duplicate journeys or notices.

## Where Drop off appears

**No separate drop-off route assignment is required.** The pupil uses the existing assigned bus route.

1. Record the school pickup outcomes and close the pickup journey after the appropriate pupil/vehicle checks.
2. In the pupil's Home journey section, select **On home bus** when the pupil boards.
3. **Drop off** is visible in the card. Before boarding it explains the required step. After boarding, it becomes actionable once today's collector authorisation is approved.
4. The parent submits the collector request through the existing family pickup-authorisation feature, and the school approves it. The driver then chooses that collector, physically checks identity, records the handover note and enters a one-time guardian code if the school requires it.
5. Confirm the drop-off. The pupil record and linked parent transport page update through the same data source.

A missing approval is explained beside the disabled Drop off control. Boarding/home departure cannot bypass an open pickup, and a pupil already on board cannot simply be changed to non-travel. Existing coordinator-only older-journey review remains in place. Plans can be closed once every pupil has a terminal outcome; this closes a record and does not claim GPS-verified vehicle movement.

## Staff attendance is now at the top of staff pages

The shared **My staff attendance** bar appears near the top of employee dashboards, before notifications. It is also available on staff chat, driver, HR, teaching and service pages.

- **Clock in** records today's arrival in WAT without leaving the current page.
- The control changes to **Clock out** after arrival is saved. After departure, it shows both recorded times.
- **My attendance history** expands to show the latest ten recorded dates.
- A save made during an attendance refresh is queued and completed rather than silently ignored. Repeated requests retain the original timestamps instead of creating another attendance row.

Tested employee specialisations include driver, teacher, HR/payroll, warden, librarian, school store, communications, Admissions and an employed school administrator. Other specialisations using the normal Staff account role use the same control. Admissions was a genuine role-access gap: it now has employee attendance and a linked self-employment view, and HR can explicitly link an Admissions login in the staff register. It does not gain HR management permissions.

### Eligibility

A staff/teacher/Admissions account must be active and explicitly linked to one HR employee record with **active** or **exiting** employment, with its start date reached. If that link or activation is missing, the bar explains what HR needs to correct; it does not silently create staff/payroll records or grant authority. An employed school administrator can use the control when linked to HR. A school owner without an employment record is not automatically treated as a salaried employee.

Parent, student, partner and platform administrator accounts do not get school staff attendance controls. The server identifies the signed-in user; a form cannot clock another employee by supplying a different user ID. An old-day form cannot silently create a new day's punch. HR-verified absence/leave/excused classifications remain separate from captured clock times, and the widget identifies those classifications when relevant.

This is one arrival/departure record per WAT calendar day, not a new biometric, GPS/geofence or overnight shift engine. Signing out of the portal does not automatically clock out. Existing HR correction, independent review, payroll and automatic day-close rules remain in place. Clocking in does not automatically change a salary or grant administrative access.

[Mobile attendance preview](SchoolOS_5.3.17_Staff_Clock_In.png)

## Installation

1. Back up application files and database and test on staging. Coordinate the update so users are not submitting records while files are being replaced.
2. Install **SchoolOS_5.3.17_Transport_Staff_Attendance_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.17**, then refresh driver, parent and staff tabs.
4. Check the attendance bar at the top of a driver/staff page. For an existing active linked employee, Clock in should be available unless already recorded today.
5. Test Not travelling home while pickup remains open, then close pickup and continue through home boarding and an approved handover using test accounts.
6. Check an Admissions login and other staff specialisations, plus HR's view of the saved attendance row.

Existing accounts, assignments, school pickup records, parent chat, messages and history remain. No schema migration, provider or new attendance subscription is required. The package is cumulative and updates the CSS/JavaScript asset versions. Bus records and staff clock times remain separate datasets.

## Rollback

File rollback retains business data and does not reverse recorded clock punches or parent notices. Complete/reconcile current **planned and active** home records before reverting: the older version does not support the new planned-journey state. Keep the database backup if business-data restoration is required. Reverting also removes the Admissions role fix and shared attendance bar.

[Validation report](SchoolOS_5.3.17_Validation.md)
