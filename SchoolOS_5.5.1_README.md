# SchoolOS 5.5.1 — Clear package recommendations

Install **SchoolOS_5.5.1_Clear_Package_Recommendations_Update.zip** through Platform Super Admin → Updates & Plugins after taking a matching files/database/key backup. This is a cumulative 43-file update. No new schema or reconfiguration is required.

The earlier pricing page repeated the same entered pupil count across every pupil-priced package. If all packages shared the same rates and minimum, every card correctly displayed the same charge, but the presentation made the school-size packages confusing. Capacity is a limit, not the number of pupils being purchased and not a per-pupil rate.

The page now shows one recommended pupil package: the smallest published capacity that fits the entered count. It calculates that package's saved rates and minimum. It does not invent higher prices for larger package names or overwrite your configured rates. Where equal capacities exist, the lower calculated charge is preferred, followed by a stable package ID tie-break.

- One school-size estimate and a separate one-calendar-month trial card.
- A visible explanation when the minimum term charge sets the price. With the suggested ₦30,000 term minimum, one pupil still costs ₦7,500 monthly; this is explicitly explained.
- A collapsed capacity/staff/price comparison. Smaller packages are marked unsuitable rather than offering an undersized selection.
- Trial and paid registration links carry the recommended package, exact count and selected cycle. Counts are no longer clamped to a smaller trial package.
- Schools above all published capacities are directed to a custom quote and trial arrangement.
- Fixed-price packages remain separate alternatives in mixed catalogues. Existing fixed-price-only catalogues remain supported.
- Package settings label maximum pupils as a capacity, not a price, explain what determines the amount and show read-only saved examples at one pupil and full capacity. Unsaved edits do not pretend to be saved prices.
- Phone/tablet layouts, dark-theme fields and an internally scrolling comparison table avoid page-wide overflow.

## What to do after installing

Refresh Pricing and enter an actual school size. Your configured package capacities determine the recommendation. For example, capacities of 150, 500, 1,500 and 3,000 recommend Starter for 1–150 pupils, Standard for 151–500, Premium for 501–1,500 and Enterprise for 1,501–3,000. These are recommendations based on capacity; the actual saved tariff still determines the charge.

In **SaaS Control Centre → Packages**, review each package's maximum pupils, pupil rates and minimum. Change rates or minimums only if you intend different charges. Changing capacity alone does not change the tariff. You do not need to make up price differences just to distinguish package cards.

Existing school agreements, accepted quotes, discounts, affiliate terms, payment verification and upgrade calculations are retained. This update changes pricing presentation, recommendations and explanatory settings text. It does not automatically change live package prices, impose new fees, migrate contracts or install itself on the hosted site. The 5.5.0 commercial foundation and provider/service boundaries remain in effect.

## Validation

Owned fictional records covered the 1/150/151/500/501/1,500/1,501/3,000/3,001 boundaries; equal and different saved tariffs; disabled plans; malformed counts; minimum-charge explanations; comparison links; trial/registration continuity; and unchanged progressive billing arithmetic. GET rendering was checked not to rewrite plans, rates, agreements or school records.

Browser checks used desktop, 390px phones and 768px tablets, light/dark themes, root and subfolder URLs, the actual registration form and authenticated package editing. Changing a test package's capacity left its one-pupil saved price unchanged. All 11 recommendation checks, 20 browser checks, 39 PHP syntax checks and 5 updater/recovery checks passed. The update's file hashes match its manifest. The owned audit database, private fixture configuration/keys and local test server were removed after testing.

No hosted school, real payment or provider account was changed during validation. The updated built-in user guide explains the recommendation and the difference between capacity, rates and minimum charges.
