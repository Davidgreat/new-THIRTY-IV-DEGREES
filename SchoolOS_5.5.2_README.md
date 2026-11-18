# SchoolOS 5.5.2 — Clear billing wording

Install **SchoolOS_5.5.2_Clear_Billing_Wording_Update.zip** through Platform Super Admin → Updates & Plugins after taking your normal matching backup. This is a cumulative 43-file update; no database migration or package reconfiguration is needed.

The price breakdown now says **Monthly payment**, **Termly payment** or **Annual payment**, instead of Selected cycle. Monthly calculations explicitly show the term total divided by four months. Under the payment amount, it says **One billing term = 4 months**. Annual calculations also clarify **One billing year = 3 terms (12 months)**.

For the 500-pupil example, the monthly breakdown reads:

- Term total: ₦232,500.00
- Monthly calculation: ₦232,500.00 ÷ 4 months.
- Monthly payment: ₦58,125.00
- One billing term = 4 months.

This is a presentation change. Saved rates, discounts, payment amounts, existing school agreements and provider verification are unchanged. The shared wording is used on public pricing and the billing rate breakdown. The built-in guide is updated.

Verification: PHP syntax passed for the edited PHP files; the monthly, termly and annual breakdowns were rendered against the existing 500-pupil figures. All 43 runtime hashes match the manifest, and private configuration/keys are excluded. No database, hosted school or payment provider was contacted or changed for this wording adjustment. The ZIP must be installed on the hosted site before it appears there.
