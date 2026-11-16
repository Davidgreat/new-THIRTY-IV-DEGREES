# School-store audit — 5.3.24

Scope: available application source and local PHP/MySQL/Chromium tests with fictional records. The user's authenticated hosted browser session was not accessible here.

| Finding | Change |
|---|---|
| Generic staff home; inventory/procurement/assets mixed on one dense page | Focused store overview and role navigation. Asset accounting is a separately authorized destination. Procurement reviewers have approval-specific controls. |
| Item creation started at zero stock and needed a separate adjustment | Item and opening stock save together; actual supplier receipts use approved purchasing. |
| No clear size/variant or item code workflow | Optional variant/code/location details; separate item identity for sizes/editions. Duplicate names/codes and repurposing an ordered variant are checked. |
| Large ID-heavy order/purchase forms | Bounded name searches, contextual actions and a guided restock request → supplier → approval → receipt flow. |
| Staff-entered customer orders disappeared from the parent's own-order filter | Parent views include the linked child's school-entered orders. Cancellation remains restricted to the requesting parent's own pending request. |
| Collection relied on paid status alone | Checks matching child, order reference and amount, plus settled balance. Collection creates a zero-unit event and does not consume stock twice. |
| No completed unpaid-reservation cancellation path | Finance-only unpaid invoice withdrawal, ledger reversal and a separate stock release. Pending payments/active checkouts block withdrawal. |
| No physical return handling | Whole-order returned goods are recorded; only verified resalable units restore availability. Damaged returns remain traceable. Refunds/credits remain a Finance decision. |
| Weighted receipt cost omitted reserved goods still held in store | Cost averaging includes those reserved units; legacy missing item metadata is handled. |
| Counts could be recorded but had no safe correction flow | Explicit audited correction, once per count, rejected if stock changed after the snapshot. |
| Supplier order could be approved but not clearly declined | Independent decline retains history and requires a revised restock request. |
| Void invoices could still inflate debt views or be refreshed | Payment/refresh guards and exclusion from financial/dashboard outstanding/forecast queries. |
| Parent shop stopped at the first 200 items | Searchable school-wide listed items with a bounded result list. |
| Little operational visual reporting | Stock-health donut, actionable counts, 14-day movements, readable daily counts and current order states. |

## Connections verified

- Shared inventory and movement register; no parallel stock database.
- Child-scoped family shop orders and Finance invoices; in-platform approval/collection/return notices.
- Payment confirmation through existing Finance payment/journal functions. Stock staff do not mark invoices paid.
- Independent request/order approval. Approved receipts update stock, moving cost and supplier payable journal once per reference.
- Physical returns and unpaid releases are distinct from cash refunds.
- Existing attendance, school chat, parent privacy and librarian workflows are preserved.

## Access and interpretation

Staff APIs require a fresh active school account, assigned store/procurement access and the session security token. Student search requires Stock manager capability. Every item, order, supplier, count and invoice is school scoped. Parent/student/librarian accounts without store assignments cannot use store management APIs or actions.

Available units exclude reserved family goods. Charts count item health and changes in availability, including reservations; collected stock is not deducted twice. Current state totals are not lifetime sales. Available-stock carrying value does not represent cash, profit, or complete inventory cost-of-sales accounting. No tax treatment is guessed.

The return flow covers all units in an order. Partial exchanges, cash-refund decisions, tax/accounting policy and opening balances require school/Finance review. The update does not automatically repair old counts, issue external payments or certify statutory compliance.

After installation, verify actual stock, supplier data, prices, role assignments and school payment/return policies. Test a real school's own request-to-collection process on the hosted platform. Local validation is recorded separately.
