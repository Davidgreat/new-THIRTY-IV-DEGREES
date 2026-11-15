# School OS 5.3.22 validation

Local PHP/MySQL and Chromium; isolated fictional school data was cleaned after testing. Production school records were not changed.

## Workflow/access: 15 checks passed

1. One-step title/copies entry with optional author/ISBN.
2. Invalid ISBN or copy count leaves no partial title.
3. ISBN-10/13 equivalent edition refused; editing preserves stock and configured charges.
4. Bounded school-only name/catalogue searches; non-librarians refused.
5. Direct checkout creates issued record, decrements available copy once and appears on linked parent's book page; duplicate active borrowing refused.
6. Renewal changes due date without stock mutation; waiting reader blocks renewal.
7. Queue priority and atomic checkout/fulfilment.
8. Return adds one shelf copy; repeated return refused.
9. Overdue renewal refused; reviewed fine creates one balanced Finance invoice.
10. Confirmed loss/replacement charge and found-copy recovery; lost-book overdue fine refused.
11. Inconsistent return refused; explicit counted-shelf reconciliation restores valid count without inventing total copies.
12. In-platform reminders reach linked recipients and are suppressed on repeat that day.
13. All manager/legacy-mapped views render populated data without PHP warnings.
14. Digital licence dates, seat limits, release/borrow and disabled-resource refusal remain connected.
15. Parent/student staff mutations and staff dashboard requests denied.

## Browser: eight checks passed

- Login opens library overview with six live metrics and pie chart.
- Book form adds actual copies with no typed record ID.
- Name-search checkout works; separate parent browser sees the same book loan.
- Contextual renewal and return complete; stock returns to the expected count.
- Equivalent ISBN identifies the existing school edition without an external lookup.
- All eight manager views fit a 360px phone viewport without document-level horizontal overflow. Light/dark previews inspected.
- Authenticated overview refresh API returns current chart HTML; selected label generates a print PDF containing the chosen title.
- Parent staff-search API request returns HTTP 403 and no student roster; parent service URLs still resolve to limited family view.

Final search/pagination, stock-review and resource/charge-log rendering were also exercised by the server checks. Camera scanning uses browser/device capability detection and was not tested with physical hardware; typed/USB input remains available.

## Regression and package

651 authenticated page visits across 14 existing demo roles passed, with no detected PHP warnings, fatal/parse errors or undefined function/method errors.

Changed PHP files pass syntax checks; JavaScript passes syntax validation. The cumulative archive has 30 application files plus the release hash manifest, with no configuration, keys, database dumps, audit scripts or synthetic records. No database migration is required.

## Existing updater: five checks passed

- Injected failure restores every file.
- Complete installation matches manifest hashes, preserves configuration and commits its journal.
- Duplicate same-version install refused.
- Explicit rollback restores original files and 5.3.21 metadata.
- Archive traversal entries refused before mutation.

This is local implementation/package evidence. Real school accounts, shelf counts, publisher permissions, device camera/physical printer behavior and live provider settlement need hosted verification after installation.
