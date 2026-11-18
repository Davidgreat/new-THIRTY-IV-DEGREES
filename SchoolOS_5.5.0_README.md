# SchoolOS 5.5.0 — Pupil pricing & commercial foundation

This cumulative 43-file update connects editable pricing rules to the public pricing calculator, registration, school billing, verified payments, upgrades, referrals and the user guide. It retains existing fixed-price school agreements.

## Install and publish your packages

1. Back up matching application files, uploads, database and private encryption keys. Install **SchoolOS_5.5.0_Pupil_Pricing_and_Commercial_Foundation_Update.zip** through Platform Super Admin → Updates & Plugins.
2. Open **SaaS Control Centre → Packages**. The commercial tables are prepared additively here, outside payment transactions. Existing school records and saved enrolment prices are retained.
3. Open an existing package and choose **Progressive pupil pricing**, or create an unpublished draft. The form shows the fields for the selected model. Review its pupil/staff capacities, band limits, rates, minimum, annual discount and service terms. Save and make it active when ready. Fixed-price fields are retained but do not set pupil-model charges.
4. Preview the public **Pricing** page with several school sizes and billing cycles. Retire old public packages you no longer want to sell; existing fixed-price enrolments can still renew their saved terms.
5. Open **Edit affiliate terms, founding offer & assisted setup** to configure new commercial terms. Enable the affiliate programme separately in its existing programme settings, after checking provider setup. Founding and assisted-setup offers start disabled.
6. Use **Offer a school-specific package** for a negotiated large-school tariff: prepare an unpublished pupil-priced package and offer it to the school. Only that school can select the private offer, and its owner must accept a quote before payment. A school needs its linked owner subscription for this self-service path.
7. Check the registration, trial, exact payment verification, callback and refund/reconciliation paths with your actual hosted configuration before taking live subscriptions. The local validation below uses fictional records and mocked provider responses; it does not install this ZIP on the hosted site or certify a live provider.

## Suggested editable tariff

| Pupils in this band | Per pupil / four-month term |
| --- | ---: |
| First 150 | ₦500 |
| Next 350 (151–500) | ₦450 |
| Next 1,000 (501–1,500) | ₦400 |
| Next 1,500 (1,501–3,000) | ₦350 |

Each rate applies only to its own band. Suggested minimum: **₦30,000 per term**. Monthly billing is one quarter of the term amount, rounded up to a kobo. Annual billing is three terms less the configured upfront discount, suggested **10%**. A billing term is four months; this release does not infer a school's academic term dates. Above a package's self-service cap, request a custom quote.

At these settings, 500 pupils cost **₦232,500 per term**, or **₦627,750 annually**. No new tariff is published simply by installing this release. Review and save each package's pricing model first. Keep the separate **one-calendar-month free trial**; paid-package selections do not include that trial. Separate legacy registration routes retain their configured trial policy.

## School agreements and upgrades

Registration declares pupil places and validates the shown tariff on the server, including a second check under the package lock. A pupil login is not another billable pupil. Billing counts active enrolled student records, excluding pending applications, withdrawn pupils and alumni. Schools receive an owner notice when active pupils exceed saved places; there is no automatic debit or automatic removal of pupil records.

Pupil-priced schools review immutable 15-minute quotes. Renewals can change the future pupil count and billing cycle, but cannot go below current active records. Additional places and compatible package upgrades charge only the unused normal-rate difference across remaining paid periods and retain the renewal date. Future prepaid periods retain their own pupil counts, so prepaying a larger future cycle does not grant unpaid extra current places. Count reductions occur at renewal; package-capacity downgrades are refused.

Existing fixed-price schools retain their saved rate and existing upgrade flow. They can explicitly accept pupil pricing for the next cycle, carrying forward their paid time. Existing pupil holders can renew a retired pupil package. Switching a used pupil package back into the fixed model is refused; create a separate fixed package instead.

## Founding schools and referrals

The founding offer is configurable and initially disabled. Suggested settings: first **20 qualifying paying schools**, **20% off** for the first paid year, maximum **500 pupils**. Registrations and trials do not claim places. A quote temporarily reserves a place for 15 minutes; only a verified first payment awards it. Renewal terms and exact savings are shown before payment. Normal rates apply after 12 months from the first paid service period. Extra places use saved normal rates rather than promotional rates.

New referrals snapshot their percentage and eligible paid-month allowance, suggested **20% for the first 12 paid service months**. One annual payment consumes 12 months; a four-month term consumes four; a monthly payment consumes one. Unpaid gaps do not consume months. Partial eligibility is prorated by service dates. Eligible upgrades are tied to covered paid periods. At the suggested 500-pupil annual price, 20% is **₦125,550**, before costs and taxes; this is arithmetic, not a profit claim.

Commission applies to eligible collected subscription money after discounts. Trials, free plans, unverified payments, unapplied review receipts and optional services are excluded. Existing referrals keep their earlier frozen terms. Existing holds, environment-scoped balances, verified bank details, payout verification and refund reversals remain in place. Test payments do not consume live founding places or live referral allowances. A test-paid school needs a reviewed clean agreement before live billing.

## External services and assistance

Core software is separate from SMS, AI, media hosting and extra storage. Configure and fund the required provider accounts and respect their quotas. Internal messaging budget units are not provider funds. This update does not invent automatic metering or provider charges, nor promise unlimited external usage. Edit package service terms accurately.

Optional assisted migration/training has an editable one-time quoted fee. A school requests it in Billing and the platform receives a linked Helpdesk case. The team confirms scope, delivery and payment arrangements before work. The request itself does not charge a card, extend a subscription or earn affiliate commission.

## Payments and recovery

Exact NGN amount, reference, payment environment and quote payment time are verified on the server. Duplicate callbacks cannot apply a quote twice. Late, stale, cancelled-but-later-paid or suspended-school payments are recorded for support review without changing the existing subscription or removing suspension. The school is told not to pay again.

Unstarted quotes can be discarded. Provider-confirmed failed, abandoned or reversed checkouts can be closed as unpaid; a merely pending checkout cannot. Funds subsequently confirmed against a closed reference go to review. Full provider refunds must be recorded against the original transaction before the Super Admin closes a refunded review, using current-password confirmation. That closing action never transfers money.

Published pupil tariffs, agreements, orders, new referral terms or activated commercial settings prevent unsafe file-only rollback below 5.5.0. Use a reviewed matching database/file recovery if necessary. Partial loss of commercial ledgers refuses default reconstruction or commission calculation. No private configuration, uploads, keys, database credentials or test fixtures are included in the update ZIP.

## Validation

Validation used an owned isolated fictional database, desktop/mobile browser sessions and mocked payment evidence. It covered pricing boundaries and minima, registration snapshots, real authenticated editor/billing forms, prepaid coverage, upgrades, affiliate credits and exhaustion, founding limits, concurrent callbacks and offers, test/live separation, refunds, cancellation, suspension and incomplete-schema recovery. The retained fixed-price upgrade regression also passed.

The prior 5.4.12 updater installed all files with matching hashes; injected failure recovery, repeated-version rejection, rollback before commercial activation, unsafe rollback refusal after activation and traversal rejection passed. PHP syntax and JavaScript syntax passed. Exact check results are supplied in the validation JSON and evidence archive.

The built-in guide now includes **Packages, pupil pricing & subscriptions**, with role-specific updates for school owners, platform operators and partners. No hosted school or live provider account was changed during these tests.
