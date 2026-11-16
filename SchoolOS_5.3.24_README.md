# School OS 5.3.24 — School-store workspace

[Download the installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.24_School_Store_Workspace_Update.zip)

A focused store desk for school uniforms, books for sale, stationery and supplies. Clear item cards, searchable student/item selection, family orders, restocking, stock counts and reports replace the mixed operational screen. Asset depreciation remains in its separately authorized workspace.

## Install

1. Back up application files and database.
2. Download the ZIP using GitHub's Download raw file button.
3. Upload and install through Platform Admin → Core updates.
4. Refresh the school-store account. Existing Stock manager permission is required. Assign Procurement approver access to an appropriate separate reviewer for independent purchasing decisions.

The cumulative package preserves existing records and prior updates. It contains 32 application files plus a release manifest, with no configuration, credentials or test data. No new tables or paid services are introduced. Item codes/variants/locations use existing school setup storage. Current asset versions load the updated UI.

## Daily store workflow

- **Overview:** Six actionable metrics for items, available units, low/no stock, new family orders, paid orders ready to collect and reserved units. Stock-health pie and 14-day availability-movement bars. Charts refresh every 30 seconds while visible, pausing while the user is reading an expanded chart detail or using its controls. Empty charts are supported.
- **Items & stock:** Add name, group, opening units/cost and selling price. Listing in the family shop requires a positive selling price. Size/colour/edition, item code, category, location and reorder level are kept in optional details. Give each size/edition its own item. Editing preserves quantity and carrying cost. Referenced corrections and school-use issues are available on each item card.
- **Family orders:** Parents request listed items for a linked child, or authorized store staff enter an order for a student. Approval atomically reserves units and creates that child's Finance invoice. Parents see school-entered orders too, but can cancel only requests from their own account before approval. The parent shop has name/size search across listed stock rather than a fixed first-200 list.
- **Collection:** The order's invoice must match the child/order/amount and be fully settled. Finance's actual recorded-payment confirmation enables Record collection. A misleading paid flag with an outstanding balance is refused. Collection records an event without deducting stock again.
- **Full physical returns:** Record that all order units have actually returned, their condition and whether they may be offered again. Resalable units return to availability once. Damaged returns are recorded without becoming saleable stock. Refunds/credits stay in Finance; none is automatically promised or sent. Partial exchanges require school/Finance review.
- **Unpaid cancellation:** School administrator opens Finance → Invoices → Withdraw an unpaid school-shop invoice. Only uncollected invoices with no pending/confirmed payment or active checkout on record qualify. Withdrawal reverses its unpaid invoice position. The storekeeper then uses Release reserved stock. Paid orders need Finance review instead. Withdrawn invoices cannot be paid or revived by refresh and are excluded from outstanding dashboards/forecasts.

## Restocking and supplier records

1. Request more units by selecting an item and entering the quoted unit cost/reason.
2. A different authorized reviewer approves or declines the request.
3. For an approved request, choose a supplier by name and send its order for approval.
4. A different authorized reviewer approves or declines the supplier order. Declined records remain in history; create a revised request if needed.
5. Record approved deliveries against the order lines. Partial deliveries are supported; a repeated delivery reference cannot add stock or supplier payable twice.
6. Fully received orders can have an actual external supplier payment reference recorded by the school administrator. The software records the ledger entry; it does not initiate a bank transfer.

Suppliers have a short contact form and an active/inactive choice. Weighted unit cost on receipt includes goods still reserved but physically held for families. Missing legacy item metadata is prepared on receipt. Opening stock records do not create supplier bills; the school's opening accounting balances remain a separate Finance responsibility.

## Counts, reports and boundaries

Physical counts cover available, unreserved units; keep reserved family goods separate. A count is recorded without altering stock. Applying a verified correction requires a matching current snapshot, so stock movement after the count forces a recount. Corrections are referenced and cannot be applied twice.

Stock history records opening units, receipts, reservations, collection events, release/returns, corrections and school-use issues. Reports use current order positions and real movement timestamps. A zero-unit collection event is intentional. Carrying values are operational estimates of available stock, excluding reservations; they are not profit, cash receipts or a complete cost-of-sales accounting statement. Payments and refunds remain in the existing Finance records.

Storekeeper landing/navigation is role specific. Teacher, librarian and primary Driver/HR/Warden dashboards retain their roles. Asset-register/depreciation tools appear separately only for accounts assigned those duties. Procurement-only reviewers get approval-oriented controls and cannot query the student roster or mutate stock.

## Verification

Local workflow tests cover opening stock, family visibility, reservations/invoices, payment gates, collection/returns, Finance withdrawal, supplier approvals/receipts and count corrections. Browser tests exercise the real parent → store → Finance → collection chain, returns and unpaid cancellation, plus all eight views at 360px. See audit/validation reports. This session has not installed the update on the hosted school or moved real money.
