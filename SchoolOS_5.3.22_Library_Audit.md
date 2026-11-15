# Librarian portal audit — 5.3.22

Scope: available source and local PHP/MySQL/Chromium tests. The companion page supplied no authenticated live document, so this is an implementation/package review rather than confirmation that the hosted school has already been updated.

| Finding | Implemented improvement |
|---|---|
| Librarian main dashboard was a generic staff page | Library overview with relevant navigation, quick actions, current records, charts and attendance/chat continuity. Primary Driver/HR/Warden roles retain their existing landing page. |
| Add-title form created zero copies and needed a separate stock form | Title/copies saved together in one transaction; optional author/ISBN/shelf and collapsed optional charge settings. |
| Book IDs and loan IDs were manually entered in routine work | Searchable student/book selection and contextual actions on each loan/book card. IDs stay in validated hidden fields. |
| Catalogue filtering loaded only the first thousand titles | Database search with bounded, paginated result sets. Reservations, digital resources and labels also have searchable pages. |
| Repeated ISBN could create another edition record | Local checksum validation and equivalent ISBN-10/13 duplicate check under a school lock. Editing retains copies and active loans. |
| No clear direct checkout or renewal workflow | Direct checkout reuses requests where present; renewal requires later date/reason and respects waiting readers and overdue review. |
| Inventory drift could overstate shelf copies on return | Stock invariant checks and explicit, audited physical-count reconciliation. No automatic legacy data repair. |
| Lost-book fine eligibility could continue accumulating after loss | Lost loans excluded from new overdue fine assessment; replacement/found workflows retain invoices for Finance review. |
| Loss/charge action was hard to interpret | Explicit lost-copy confirmation and configured replacement amount; reviewed charge preview and current library invoice log. |
| Queue order and relevant student were hard to follow | Named queue cards, position, availability and prefilled lending; transaction rechecks queue priority. |
| Reports lacked a focused operational view | Physical-copy donut, six actionable totals, 14-day request/return chart, readable daily counts and current loan states. |
| Label tool printed a broad catalogue set | Search, selection and PDF/print of chosen labels. |
| Large forms and dense controls were awkward on phones | Scoped glass surfaces, short labels, responsive cards, bounded search results, scrollable navigation/tables and light/dark contrast. |

## Relevant feature set

Books and shelf counts, student requests, checkout/returns, reservations, overdue reminders, reviewed fines/replacements, digital licences, history, reports and labels are library responsibilities. General payroll, transport, procurement and communication-provider controls are not included in the library working navigation. Other workspaces appear only when the same account independently holds the relevant permissions.

Book-entry basics are intentionally limited to what the librarian knows. ISBN is optional for local/unnumbered school books. Author/location can be filled later. Pricing is optional and does not bill anyone on book creation. No paid metadata lookup was added.

## Connected records and permissions

- Uses existing `books`, `lib_meta`, `lp_library_loans` and reservations. Student requests and parent book pages see the same loan states and due dates.
- Charges use the existing Finance invoice/journal path. Duplicate charges are prevented by loan/kind. No automatic payment/refund occurs.
- Returns/loss/recovery and checkout lock the book/loan as needed. Reservation consumption and checkout commit or roll back together.
- Active account and Librarian capability are checked for staff search/API access; requests require the session security token. All data is scoped to the school.
- Parent and ordinary student accounts cannot open staff roster search or perform library management actions. Parent library restrictions from 5.3.21 remain intact.
- Reminders target active accounts whose current parent/student role matches the explicit child relationship; repeated same-day reminders are suppressed.
- ISBN/QR scanning is a convenience for identifying catalogue entries, never proof of borrower identity or permission.

## Data interpretation and hosted follow-up

The trend uses existing creation/return timestamps; the system has no historical checkout timestamp to reconstruct. Pie counts reflect recorded physical stock; discrepancies are flagged, not concealed. Overdue invoices are reviewed, one-time assessments and do not grow automatically after recording. Recovered/lost invoices require Finance review.

After installing, verify actual copy counts, Librarian assignment, real child/account links, school charge policy and any digital licences. Test a real book request, checkout and return against that school's data. Camera hardware, physical printers, publisher authentication and real payment settlement require hosted/device checks; the provided tests validate the local workflows and installable package.
