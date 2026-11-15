# School OS 5.3.21 — Parent books & access

[Download the installable update ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.21_Parent_Books_Access_Update.zip)

Parents now have a focused **My children’s books** page inside Family Space. The generic **Library & school store** services menu has been removed for parents. Librarian and other staff workspaces remain available to their authorized accounts.

## Install

1. Back up application files and database.
2. Download `SchoolOS_5.3.21_Parent_Books_Access_Update.zip` using GitHub's Download raw file button.
3. Upload and install through Platform Admin → Core updates.
4. Refresh the parent portal. Application asset URLs were versioned so browsers load the current portal styles/scripts.

This cumulative package includes the previous parent dashboard/report-card and collector updates. Existing accounts, loans, reservations, charges, orders, contacts and consent records are retained. No new database tables, providers or fees are introduced.

## Parent experience

Open **Family Space → Learning & progress → My children’s books**, then choose a child.

Parents see only that child's:

- Current borrowed books and requests, with understandable status labels.
- Return dates and an overdue reminder when the recorded date has passed.
- Previous borrowing and return records.
- Existing book reservations, as read-only status/history.
- Actual school-issued overdue/lost-book charges and a link to existing fee invoices/payments.

The page does not calculate or assess fines, issue/return books, manage copies, reserve new books, scan catalogues, show ISBN administration or expose other families' records. Most recent 100 loans, 100 charges and 50 existing reservations are shown. The school librarian/student workflow continues to manage borrowing. Learning resources explicitly shared with families remain available through Family Space documents and homework; parents no longer browse the general library resource/ebook catalogue or use its raw resource endpoint.

## Useful customer functions kept separate

- **Family Space → Money & receipts → School shop:** School-listed items and prices, requests for the selected linked child, the requesting parent's own order statuses, cancellation of unapproved requests and a link to Finance for issued invoices. No procurement, supplier, cost, stock management or asset controls.
- **Family Space → Permissions & files → Contact & message preferences:** The parent's own contact update and external-message choices for their account or the selected child's valid student account. No campaigns, provider configuration, delivery logs or messaging credits.
- Community Hub remains the parent location for published announcements/events/polls. Private conversations stay in the existing Family & school chat.

## Direct-link and server rules

Old parent services links are handled deliberately:

| Old link | New destination |
|---|---|
| General services or any library tab | Family Space → My children’s books |
| Inventory / procurement / assets tabs | Family Space → School shop |
| Engagement consent/contact tab | Family Space → Contact & message preferences |
| Engagement messages tab | Family & school chat |
| Other engagement tabs | Community Hub |
| Website/CMS or access controls | Denied |

Parent service submissions use a small customer-action allowlist. Catalogue, library issue/return/fine/resource actions, stock/approval/fulfilment, provider and website management requests are rejected server-side. Generic library render/resource functions also guard parent access. Old URLs are not a route back to staff tools. Child and tenant links are rechecked, including cancelling an earlier order after a child link has been removed.

## Validation

30 server workflow/regression checks, seven browser checks, 638 authenticated role-page visits and five updater/rollback checks passed locally. Phone layouts were checked at 360px. The download includes application files/manifest only, not credentials, synthetic records or test scripts. This session has not installed the update on the hosted site or settled a live payment.
