# Parent portal audit — School OS 5.3.20

Scope: available application source and a local PHP/MySQL copy with synthetic school records. The authenticated live browser session on getschoolos.com.ng was not accessible in this workspace. Findings below distinguish implementation verification from production sign-off.

## Findings addressed

| Finding | Change |
|---|---|
| Generic role landing page and scattered family links | Parent login now opens the family overview used by Family Space. Each child has clear record/chat shortcuts. |
| Parent–child chat existed but was hard to find | Direct shortcuts for every correctly linked active student account; child-specific conversations use existing verified permissions. |
| Result tables separated from printable cards | Published-term selection, weighted subject detail, performance bars, assessment breakdown and direct print/PDF link. |
| Minimal print branding | Saved school logo, colour, name, motto, address/contacts and approved format block order. |
| Parents could request any approved school design | Parent/student print access now requires the selected child's assigned approved class format. |
| Complete-looking card could omit an entirely unapproved subject | Completeness check compares configured assessed subjects with complete approved results. Missing or mismatched components block printing. |
| Generic grade labels in parent results | Complete report grades use the approved school's bands; incomplete results do not receive invented grades. |
| No dedicated teacher/head report comments or term date source | School-admin report notes connect real approved text, explicit attendance period and resumption date to the learner/session/term. |
| Hidden staff-only documents/consent could be requested by guessing IDs | Download and response handlers now enforce the same staff audience restriction as the visible page. |
| Parent homework missed online activities | Adds published/released LMS homework and child-specific submission/graded feedback, retaining delivered academic homework. |
| Timetable and library loans not surfaced in Family Space | Dedicated current-session timetable and child-scoped book log. |
| Attendance was a static list | Date filter, recorded-state donut and detailed daily log. |
| Fee chart could include void/cancelled invoices | Excludes those invoices; parent checkout refuses cancelled invoices. |
| Mobile/dark theme hierarchy and contrast | Scoped glass surfaces, responsive grids, readable typography, focus states, scrollable tables and explicit contrast on light hero panels. |

## Feature fit for a Nigerian school parent

| Parent need | Connected implementation |
|---|---|
| One account for siblings | Verified family links, child switcher and per-child cards; no email/name inference. |
| Academic progress | Session/term selection, school-configured CA/exam weights, grades, observations, comments and printable card. No single national grading scheme is assumed. |
| Attendance and absence | Recorded daily attendance with dates/notes, optional period logs and absence request/review workflow. |
| NGN school fees | Existing invoice balances, Paystack initialization/verification and branded confirmed-payment receipts; no new payment provider. |
| Communication | Individual child chats, assigned teacher/school contacts and scoped parent–driver chat. |
| Homework support | Released activities, due dates, child submission status and teacher feedback; parent does not impersonate learner submissions. |
| School planning | Current timetable, published events and parent–teacher appointment booking. |
| Safety and care | Existing consent, regular/one-day collectors, bus history/updates and boarding/welfare views. |
| School services | Meals, library books, published documents, support requests and parent feedback. |

## Access review

- Parent actor rechecks active login/role. Child records require an explicit tenant-scoped parent relationship.
- Child chat requires the active student account and the matching family relationship; existing thread access rechecks member permissions. Unrelated pupils, families or tenant records are not exposed.
- Parent fees and receipt access use the child's invoice/family link. Document downloads enforce published audience and child relationship checks. These existing guards remain in place.
- Report links are private authenticated endpoints with no-store/noindex headers. Only approved scores from a published class term and the permitted school format qualify. Nursery parent cards also require term publication.
- Report notes are authored by school administrators. Parent attempts to set notes or assign a class report format are refused.
- Existing transport collector approval, code policy and handover validation remain intact.

## Production checks still needed after installation

Install on the hosted platform, verify your actual family/student/teacher/driver links, school branding and report format, then publish a complete test term and print its card. Confirm your school's real attendance dates and comments. Real payment settlement and live hosting behavior were not tested against external services. Historic reports depend on the application's existing class/result records; the update does not invent historical class enrolment or recreate missing source data.
