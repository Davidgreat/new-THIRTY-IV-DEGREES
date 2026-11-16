# School OS 5.3.24 validation

Local PHP/MySQL and Chromium; isolated fictional school data was cleaned after tests. No live school record or external payment was changed.

## Workflow/access: 19 checks passed

- Store-specific landing and role limits.
- Opening stock/variant/code creation and family listing.
- Editing preserves quantity/cost; duplicate identity or unpriced listing rolls back.
- Staff-entered child orders visible to linked parent, without cancellation by a different requester.
- Atomic stock reservation and child invoice with balanced journal; unpaid/duplicate approval/collection refused.
- Partial payment plus misleading paid flag cannot authorize collection.
- Confirmed full payment enables one collection without a second stock deduction.
- Full resalable return restores units once; invoice/refund remains with Finance.
- Unpaid release requires Finance withdrawal; stock staff cannot withdraw invoice.
- Insufficient stock rolls back the invoice/journal and leaves request unapproved.
- Ordered variant identity cannot be repurposed.
- Restock request and supplier order require independent approval.
- Partial/repeated delivery references, stock counts and weighted cost including reserved goods.
- Administrator-only supplier payment recording; duplicate refusal.
- Stale count snapshots rejected; verified correction applied once.
- Damaged return does not reoffer goods; wrong invoice cannot authorize collection.
- Independent supplier-order decline retains records without receiving stock.
- Empty-school charts render safely.
- All store views render populated data; unauthorized management/search actors refused.

## Browser: eight end-to-end checks passed

1. Store login opens six metrics and stock-health pie.
2. Item form creates uniform variant, code, opening units and family selling price.
3. Separate parent browser requests item; stock approval creates child invoice; unpaid collection unavailable.
4. School administrator records and confirms payment through actual Finance forms; store records collection; parent sees collected state.
5. Full physical return and separate Finance-review state work through forms.
6. Finance withdraws unpaid invoice through its real form; store separately releases reservation; parent sees cancellation.
7. All eight store views fit a 360px phone viewport; desktop/light/dark previews inspected.
8. Authenticated dashboard summary API works; parent student-roster request returns HTTP 403 without names.

The Finance tests recorded fictional cash/payment references; they did not contact a bank or settle a real Paystack payment. Restock, role and count checks used actual application transaction functions.

## Regression and install

Authenticated page regression covers 14 existing account roles and detects PHP warnings, fatal/parse errors and undefined-function/method errors. Changed PHP and JavaScript syntax checks passed.

Five updater checks cover injected failure recovery, complete manifest/configuration/journal verification, duplicate-version rejection, explicit rollback to 5.3.23 and ZIP traversal rejection.

The cumulative package has 32 application files plus its manifest. No configuration, secrets, database records or test scripts are shipped. No new tables are required. Item metadata uses existing school setup records. Existing data is preserved; real hosting, stock counts, role setup and external settlement require verification after installation.
