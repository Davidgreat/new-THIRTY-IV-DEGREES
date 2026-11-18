# SchoolOS 5.4.9 — Prorated package upgrades

Back up matching files, uploads, database and private keys, then install **SchoolOS_5.4.9_Prorated_Package_Upgrades_Update.zip** through Platform Super Admin → Updates & tools. This cumulative 43-file release retains existing school records, settings and clean-link generation. It adds two small billing tables automatically when billing/verification is used; no credentials or test fixtures are shipped.

## What schools can do

Open **School Admin → Start my school → Subscription**, or **My subscription & upgrades** on My school day. Choose an available compatible larger package and select **Calculate my upgrade**. The quote shows the unused paid-service credit and exact amount to pay before secure checkout.

- Active paid tier upgrades keep the same monthly, termly or annual cycle and renewal date. Only the difference for remaining paid time is charged. Example: halfway through a ₦20,000 monthly plan, upgrading to ₦30,000 costs about **₦5,000**; the following renewal is ₦30,000. Exact timestamps and kobo rounding determine the quote.
- Unused service is time remaining, not a measure of pupil activity or a withdrawable cash balance. Verified prepaid future cycles are included. Each remaining period uses its recorded rate; credit is rounded down and its incremental upgrade charge rounded up to kobo.
- Trial schools can select a paid package early. There is no paid trial credit: the full paid cycle is charged, and the remaining trial time is retained before that paid period. The larger package becomes available after verification.
- An expired or configured free subscription starts a full new paid cycle, with no expired/free-service credit.
- Schools cannot downgrade price, pupil capacity or staff capacity. Same-rate capacity increases can be accepted without a payment. Billing-cycle changes are intentionally not offered in this self-service flow.

## Payment and recovery

Quotes last 15 minutes. The server checks school ownership, current saved package/rate/balance, target package and permissions again at acceptance and verification. Tampered fields cannot set price or credit. Duplicate verification is idempotent, and checkout initialization is claimed once. Subscription operations serialize per school. Payment references, NGN amount and provider environment must match verified provider evidence. Existing renewal and signed-webhook dispatch use the same upgrade verifier; affiliate commissions and platform money records use the actual upgrade payment, not the full target package price.

A payment made against an expired/changed quote is recorded as paid but does not silently alter the package. The school is told **do not pay again**, and a helpdesk case is opened. Platform → Money lists these reviews. A real Super Admin can close review after completing the actual provider refund and recording the full paid refund against the source transaction. That action checks the recorded refund; it never initiates a transfer. Uncertain/abandoned pending payments must be reconciled before another quote; references are not blindly cancelled or replaced.

Older subscriptions with verified full-cycle receipts can reconstruct coverage backwards from their saved renewal date. New payments record exact periods. Schools without a linked enrolment or provable paid coverage need platform review rather than an invented credit. Retain receipt evidence and matching backups. File-only rollback below 5.4.9 is refused once an upgrade payment reference is prepared; use a matching database/file recovery plan if needed.

Built-in owner, complete and platform guides and Pricing FAQs are updated. Validation used isolated fictional records and simulated provider responses; no real payment, email or hosted installation was performed. A real Paystack test/live end-to-end payment remains an operator check before offering upgrades publicly.
