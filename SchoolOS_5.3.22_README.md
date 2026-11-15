# School OS 5.3.22 — Librarian workspace

[Download the admin-installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.22_Librarian_Workspace_Update.zip)

A focused library desk with a short book-entry form, searchable lending, useful charts and clear actions beside each record. The same books, loans and invoices continue to power the student and parent portals.

## Install

1. Back up files and database.
2. Download `SchoolOS_5.3.22_Librarian_Workspace_Update.zip` using GitHub's Download raw file button.
3. Upload and install through Platform Admin → Core updates.
4. Refresh the librarian portal. Current asset versions load the updated styling and interactions.

Existing real/demo accounts and data are retained. The cumulative package includes earlier parent/report-card/transport updates. It adds no tables, paid integrations or external ISBN service. Existing Librarian permission is required. Staff librarians open the library overview on login; an account whose primary work is Driver, HR or Warden keeps that main workspace and can still open its assigned library module. Teachers keep their teaching overview. School administrators retain their broader workspaces.

## Daily workflow

**Add a book:** Books → Add a book. Required: title and copies received (default one; zero allowed for a catalogue-only title). Author, ISBN and shelf are optional. School overdue/replacement charges sit in a collapsed optional section and default to zero. Saving creates the title and copies together. Editing details preserves existing copies and loans.

ISBN checks validate the number locally and identify an existing school edition, including equivalent ISBN-10/ISBN-13 values. Open the existing title to add copies. No record ID is typed and no title/author is invented from an ISBN.

**Lend:** Lending & returns. Search student and book by name, admission number, ISBN or catalogue code as applicable. Choose a result, choose the return date, then Confirm lending. Existing requests can be approved directly on their cards. Searches return at most 20 names/results; the catalogue is searched in the database and paginated rather than cut off at the first thousand titles.

**Return:** Open the student's loan and select Record return. The shelf count increases once. Returned loans remain in history and on the family's book page.

**Renew:** Extend return date on a current, non-overdue loan. A later date and reason are required. Another waiting reader prevents renewal. Overdue books require a return/charge review before lending again.

**Reservations:** Search and page through the waiting list. Queue position and current availability are visible. The first waiting reader can be opened directly in lending. Queue priority is checked again inside the checkout transaction.

**Overdue:** Send today's in-platform return reminders to active, linked student/parent accounts. A loan is reminded at most once per day. Review any school-configured charge separately; a manual charge creates one existing Finance invoice. Recent library-charge invoices show their current balances. No bank/provider payment is executed from this page.

**Lost/found:** A lost-copy action explicitly confirms the loss and configured replacement charge, updates copies and creates at most one replacement invoice. Found & returned restores the copy. Finance reviews existing charges/refunds. Lost records cannot continue generating a fresh overdue fine after loss.

## Dashboard and stock review

Overview shows titles, shelf copies, books currently out, requests, due-today and overdue counts. The physical-copy donut and 14-day request/return chart use real records. Dates are WAT. The trend counts request creation dates and actual return dates; no checkout timestamp is invented.

Charts refresh every 30 seconds while visible, pausing while a chart's details are open or keyboard focus is inside the panel. Daily counts are available as text. Clicking a metric opens the relevant records.

If copy counts disagree with loans, a stock-review message appears. No old counts are silently rewritten. In Books → Review shelf count, physically count copies and check active loans. The verified shelf count plus active loans must equal total copies. This changes only the shelf count, with an audit note. Use Add/remove copies for actual receipts or removal of shelf copies. Borrowed copies cannot be removed by a normal count adjustment.

## Other relevant tools

- **Digital shelf:** Clear resource forms, provider/permission note, licence dates, ebook seats and disable access. Search and pagination retain access to the whole register. Active seats and recent access records are shown. The school still controls publisher accounts and sharing rights.
- **Reports:** Live stock/loan counts, current loan-state totals and readable trend counts. Financial figures are invoice positions, not assumed cash receipts.
- **Print labels:** Search/page through titles, select specific QR labels and print those labels. Camera scanning is optional where supported; typed ISBN/catalogue codes and USB scanners remain available. QR codes identify titles and do not authorize borrowing.
- Staff attendance and school chat remain connected to their existing functions. Librarian chat permissions are unchanged; no new private pupil-message access is granted.

## Boundaries and verification

Parents retain the limited My children’s books page. Student requests and parent loan/charge views use the same register. Staff search and management APIs require current Librarian access and a session security token. Searches, actions and reports are tenant scoped.

Local tests passed 15 workflow/access checks, eight browser checks including actual parent loan visibility and a selected-label PDF, 651 authenticated page visits across 14 roles and five installation/rollback checks. See the audit and validation reports. The ZIP contains 30 cumulative application files and a hash manifest, excluding configuration, credentials, test fixtures and synthetic records. Hosted installation is still required.
