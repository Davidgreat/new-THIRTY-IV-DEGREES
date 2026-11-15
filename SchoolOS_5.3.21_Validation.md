# School OS 5.3.21 validation

Local PHP/MySQL and Chromium tests used isolated synthetic family records. Fixtures were cleaned after testing. No live school records were changed.

## Server: 11 targeted checks passed

1. Parent navigation and service-area checks exclude generic services; student/admin access remains.
2. Old URLs map only to permitted family destinations or denial.
3. Book page shows own current/returned loans, overdue reminder, school charge and existing reservation; no other-family or catalogue controls.
4. Empty sibling state is clear; unrelated child denied.
5. Rendering books does not add charges or change available stock.
6. Parent library/catalogue/resource, staff stock/provider and website actions are denied, including direct generic resource access.
7. Customer shop includes listed items and hides internal inventory/costs.
8. Parent can request/cancel their own linked-child order; unrelated student refused.
9. Own contacts and parent-managed child message consent work; another parent's consent cannot be changed.
10. Customer actions return to the correct family view and valid linked child.
11. Removing a child link prevents old-form order cancellation and book access.

The 19 prior parent portal server checks were also rerun successfully: multi-child chat permissions, published branded reports, complete approved marks/weights, current timetable, child loans/homework, fee scope, staff-only document/consent privacy, cancelled checkout, school report notes and stale account/link denial.

## Browser: seven checks passed

- Parent menu omits generic services; old default services URL opens My children’s books.
- Every old catalogue/resources/labels/reports/loans/overdue/reservations/history URL opens the limited family book page.
- Unrelated child content is not disclosed; parent raw library-resource and staff website/access URLs return HTTP 403.
- Old inventory URL opens a simple customer shop; request and cancellation complete in Family Space.
- Old contact/consent URL opens family preferences and saves the parent's choice in place.
- Book, shop and preference views fit a 360px phone viewport without horizontal page overflow.
- Existing librarian account still sees catalogue and return-management controls.

Desktop and phone book previews were inspected. The final book/reservation display wording and data were also checked by the server tests.

## Role-page regression

638 authenticated page visits across 14 existing demo account roles. No detected PHP fatal/parse errors, warnings or undefined-function/method errors. Parent reachable pages decrease because generic staff services are no longer part of that menu.

## Installer: five checks passed

- Existing 5.3.20 updater recovers all changed files after an injected mid-install failure.
- Full installation matches all 30 manifest hashes and preserves configuration; committed transaction journal written.
- Duplicate version install rejected.
- Explicit rollback restores prior files and 5.3.20 metadata.
- ZIP traversal entries rejected before changes.

All changed PHP files pass syntax checks. The archive excludes configuration, credentials, database records and test fixtures. Real deployment and external provider settlement still require hosted verification after installation.
