# School OS 5.3.20 — Your family compass

[Download the admin-installable update](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.20_Parent_Family_Portal_Update.zip)

This cumulative update brings the parent landing dashboard and Family Space together. Existing real and demo parent accounts use the new experience after installation. Their verified child links, records and conversations are preserved.

## Install

1. Back up application files and database.
2. Download the ZIP using GitHub's Download raw file button.
3. Upload and install through Platform Admin → Core updates.
4. Refresh the parent portal. Use the child switcher to choose whose records you are viewing.

The package includes 28 cumulative application files, including all 5.3.19 collector changes. It adds no database tables, paid services or external chart dependencies. School report notes use existing school setup records. Configuration files, private credentials, test scripts and test data are excluded.

## Parent features

- **Family overview:** Every linked child, direct chat shortcuts, selected-child attendance donut, fee-allocation donut, feature cards and upcoming school events. Glass surfaces, clear labels, keyboard focus and responsive light/dark themes.
- **Family & school chat:** Open a private conversation with each linked child, assigned teachers, the school office and an eligible assigned bus driver. Chat uses the existing system, including typing indicators, emoji and reactions. A child needs an active student login correctly linked by the school; missing/ambiguous links are explained rather than guessed.
- **Results & report cards:** Choose a published session/term, see weighted CA/exam contributions, subject charts, school grade bands, individual assessment marks, observations and school comments. Legacy results remain separate.
- **Printable report:** Open the class's school-approved report format and print/save PDF. Uses configured logo, school name, motto, contacts, address and colour; preserves the design's block order. Includes learner/admission/class details, weighted CA/exam/total/grade, subject average, approved skills and configured comments/dates. Parents cannot view another child's card or choose a different class format.
- **Attendance log:** Select a date range of up to one year, see the recorded-day chart and daily school notes; recent lesson-period attendance remains available separately. Unrecorded days are not treated as absence.
- **Homework & learning:** Published, released online homework/quiz activities, due dates, child-specific submission status, marks/feedback once graded, and delivered classroom homework. Children submit from their own learning accounts.
- **Class timetable:** Current-session subjects, times, teachers and rooms.
- **Library & books:** The selected child's book requests/loans, due dates and returned status.
- Existing fees, payment verification, branded receipts, calendar, teacher appointments, absence requests, consent, collectors, transport, boarding, meals, school documents, support and parent feedback remain connected.

## School setup for printable reports

1. Configure **School setup → Branding** with the school's name, logo, contact details and colour.
2. In **School Intelligence → Academic tools → Report designer**, create and independently approve the school's format. Set nursery/primary/secondary level, block order, grade bands and the school's actual CA/exam weights.
3. In **Academic tools → Report cards → Assign a school report format to a class**, choose the class and approved format. This preserves any existing curriculum/calendar configuration.
4. Enter/moderate the student's assessments and publish the class term through existing Academics. Every configured assessed subject needs complete approved components and weights matching the chosen design.
5. School administrators can use **Report cards → School report comments & term dates** to save the learner's approved teacher/head comments, explicit term attendance dates and next-term resumption date. Saving replaces that learner/term's prior notes. These appear to parents only with a published term report.
6. Parent opens **Family Space → Results & report cards → Open school report card**.

No results, grades, comments, signatures, promotion decisions or attendance days are fabricated. If term attendance dates are not supplied, the card explicitly labels its attendance as all recorded history, not a term total. Blank school comment data is identified. A missing report format or incomplete/unpublished results produces a setup explanation instead of a misleading card. Ordinary fee access does not impose an invented report-card payment lock.

## Verification

Local checks cover multi-child privacy, real two-way chat in separate browser sessions, published report/PDF generation, school report setup, parent editing restrictions, all 20 parent views at 360px, and updater installation/rollback. See the audit and validation reports. This session did not install the package on your live server or execute a real Paystack charge.
