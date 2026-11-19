# SchoolOS 5.5.4 — Website ROI calculator

## Install
1. Keep a current backup.
2. Sign in with the real Platform Super Admin account.
3. Open Updates & Plugins. Upload **SchoolOS_5.5.4_Website_ROI_Calculator_Update.zip**, tick the trusted-source box and choose Verify & Install Update.
4. Open Website → ROI calculator. With clean links enabled, the address is `/roi-calculator`. Legacy links also work: `/index.php?page=roi-calculator`.

This is an update ZIP, not a fresh-install archive. It contains a verified release manifest and 43 approved application files, with no config, keys, uploads, test database or SQL migrations. The updater preserves school data and offers rollback.

## What is included
- Calculator links in the website menu, homepage, pricing page and footer.
- Adjustable pupils, fees, school terms, unpaid share, extra collection, admin savings and optional extra costs.
- Automatic smallest-fit package recommendation, with manual selection of another published package.
- Actual current fixed prices or progressive pupil bands from the same engine used for registration. No copied tariff table.
- Annual, termly and monthly payment options; every result compares 12 months of subscription with 12 months of benefits. Configured annual savings are applied for annual billing.
- Net annual benefit, percentage ROI, cost/benefit chart, break-even collection rate and full breakdown.
- Responsive light/dark layouts, touch controls, a mobile estimate strip and a printable report. Server-side calculation works without JavaScript too.
- Guides updated for school owners, platform operators and billing.

## When prices change
Save the package in the existing package settings page. New calculator requests use that price immediately. An already-open calculator rechecks on input changes, Calculate, and every minute while visible; returning to the tab also checks if a minute has elapsed. No additional ROI price setting is needed. Existing school contracts and accepted quotes are not changed.

## Reading the result
Potential benefit = extra fees collected + realistic admin savings. Total cost = annual subscription + extra costs. Net annual benefit = potential benefit − total cost. ROI = net benefit / total cost × 100. Negative estimates remain visible. With zero costs, percentage ROI is undefined. Collection improvement cannot exceed unpaid fees. If no package fits, a quote is requested instead of inventing a price.

The starting values are an illustration, not measured SchoolOS customer results. Collection recovers existing receivables; it does not increase fees charged. Staff time is only counted in admin savings if it actually reduces cash spending. No unproven enrolment or retention value is added. Trial months, limited offers and future price changes are not assumed. Schools should enter extra services, taxes and setup costs as needed.

## Verification
Calculation, live tariff-refresh, mobile/desktop, no-JavaScript, subfolder routing, error handling, installation, rollback and archive validation were tested locally with fictional data. No production data, messages or payments were changed.
