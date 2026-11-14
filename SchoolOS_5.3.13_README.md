# School OS 5.3.13 — HR attendance and staff profiles

## What HR can now do

**Open Assigned operations → Human Resources & Payroll → HR overview.** The operations Overview also shows the HR attendance overview for authorised HR users. The default attendance date is today in Africa/Lagos time.

- See totals and an accessible bar chart for present, recorded absent, not clocked in, on leave, excused and staff without a linked portal login.
- Choose a date to check its log. Click a total to open the matching named staff list, then open any staff profile.
- See pending leave requests and open staff queries, with links to follow up.
- In Attendance, record or correct a linked staff member's verified attendance status with a reason. This keeps their clock-in/out times and adds a private correction-history entry. Future dates and dates before appointment are refused.

**Open Staff register → View / edit.** This now opens a staff profile rather than only an editing form:

- Name, school job, department, employment stage, start date and elapsed time since joining.
- Private appointment, contact, emergency contact and qualification details.
- Daily attendance with a date-range filter, recorded-present/absent totals and dates without entries. Expand the daily log to see individual dates and clock times.
- Leave requests and decisions.
- Formal queries, staff responses and recorded HR outcomes.
- Induction, appointment/contract documents, duties, published appraisals, training/CPD, concerns, exit and attendance-correction history, wherever those records exist.
- Monthly allowances, salary advances and released payslips.
- A **Chat with [staff name]** shortcut. It opens an existing permitted one-to-one chat, or lets HR send a first message and open the conversation. A linked active staff account and activated chat workspace are required. Existing school messaging permissions remain enforced.
- An expandable Edit staff details form; no historical salary calculation is changed by viewing or editing the profile.

## Formal staff queries

In **Queries & responses**, or the employee's profile, HR can issue a private query with an optional response due date. The linked staff member reads and responds from **My employment → Queries & responses**. HR reviews the response, records an outcome and closes the query. Closed queries are read-only. Due dates are recorded for follow-up; they do not automatically issue penalties or send external messages.

Each employee sees only their own queries. HR can review school-scoped queries, and only the addressed employee can submit the staff response. In-platform notifications identify a new or updated query for the staff member; authorised HR users receive notifications for responded queries. Notification sound still follows the existing browser interaction/audio rules. This feature does not email or message external recipients automatically.

## Attendance meaning and limits

**Not clocked in is not the same as absent.** Missing entries can reflect weekends, holidays, a forgotten clock-in or a login/link issue. HR must verify absence; this update does not assume a school calendar or automatically deduct pay.

The selected-day roster uses current active/exiting employees whose start date is no later than the selected date, plus employees with an attendance entry on that date. Historical dates are not immutable historical headcount snapshots. Former staff without an entry may not appear in that day's overview; their retained records remain available through their profile. Attendance follows the staff member's currently linked login; link changes are not a reconstructed historical account map. Staff without a login are shown separately and need a link before using the existing clock-in log or manual correction form.

A manually verified present entry can have no clock time. Approved overlapping leave appears as leave when there is no recorded presence or overriding verified status. Recorded late attendance counts within present. Profile date ranges include calendar dates, including weekends/holidays, so no inferred absence rate is shown. Existing exited records do not contain a reliable historical exit date; the header says time since joining, not completed service duration. Views show bounded recent records: 100 queries, 200 leave/history records, 100 allowances/advances/CPD records and 60 released payslips. Attendance can be filtered across an approximately one-year window; older periods can be selected separately. Existing payroll, tax, leave-balance and payment limits from 5.3.12 remain.

## Installation

1. Back up the application and database and test on a staging copy.
2. Install **SchoolOS_5.3.13_HR_Attendance_Profiles_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.13**, then refresh open dashboard tabs.
4. Open HR overview, choose a date and check one staff profile. Verify its account link and compare clock times with the previous attendance screen.
5. Test a private query with a staff account and the chat shortcut. Confirm the staff member can see their own information and cannot open another person's private record.

Existing school and demo accounts use the new views after refresh. Historical data and payroll remain intact. This cumulative release includes previous HR, chat, classroom and mobile updates. No schema migration or new provider is required. New query/correction records use existing private HR storage. File rollback retains recorded business data but hides the new interfaces; it does not reverse later attendance corrections or messages.

[Validation report](SchoolOS_5.3.13_Validation.md)
