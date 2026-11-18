# SchoolOS 5.5.3 — Mobile pricing layout

Install **SchoolOS_5.5.3_Mobile_Pricing_Layout_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**, after your normal matching backup. Upload the ZIP itself. This is a cumulative 43-file update, with no database migration or package reconfiguration.

## Fixed

An older phone-only two-column card layout was squeezing the recommendation title and service disclosure into zero-width columns. That made the page display words one letter per line and pushed the price into neighbouring sections. At phone widths the cards now follow a natural single-column flow, with full-width headings, prices, disclosures and buttons. The pupil calculator and billing-cycle choices also adapt to small screens, with comfortable touch targets. Package comparison remains horizontally scrollable inside its own container.

The public stylesheet URL now uses cache key 553 so browsers request the corrected CSS after installation. Your existing package prices, pupil bands, minimum charges, subscription settings and registration selections are unchanged. Only public_site.css, its cache URL in public_site.php, and VERSION.txt differ from 5.5.2; the remaining 40 cumulative runtime files match 5.5.2 exactly.

## Verified

- 155 responsive and flow checks across 320,360,390,430,460,461,600,680,768,1024,1440 and1920px, in light and dark themes.
- Expanded calculation, service terms, included-feature and package-comparison panels remain readable and contained.
- Pupil-count calculation, monthly/termly/annual choices, trial links and paid registration handover still work.
- Long fixed-price package names and large naira amounts fit at 320,390 and844px.
- Existing 5.5.2 updater installs all 43 verified files, preserves configuration, recovers from a simulated interrupted install, supports explicit rollback, and rejects repeated installation and unsafe archive paths.

The issue was reproduced on the live public page. The preview shows the candidate CSS applied in a read-only browser, not an already deployed change. Install this ZIP on the hosted platform for the fix to appear there. No live data or settings were changed while preparing the update.
