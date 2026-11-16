# School OS 5.3.26 validation

Local PHP/MySQL and Chromium with synthetic school records. Hosted-school installation and real payment settlement are outside this session.

## New product option checks: 13 passed

- Relevant group profiles, preset sizes, format/portion controls and colour visibility.
- Automatic colour-family naming including multiple red shades, neutral colours and common hues.
- Four size–colour combinations create separate counts/codes/opening movements and one product key.
- A bad later row rolls back the complete batch.
- Duplicate combinations, fractional units and more than 60 combinations are refused.
- Books reject colour attributes; food stores portion and flavour.
- Grouped shop selectors retain exact inventory IDs and exclude zero stock.
- Parent order approval reserves only its chosen size and colour and creates the matching invoice.
- Order-history variants cannot be repurposed; ordinary edits preserve stock and attributes.
- Adding a size preserves the product identity and old units; a later duplicate rolls back all new rows.
- Parent stock mutation and foreign-school product anchors are refused.
- Shared photos resolve within the school; raw references survive ordinary edits; removal produces a placeholder.
- Creation/edit/add-option forms render their stored data correctly.

## Browser checks: seven passed

1. Group changes show relevant presets/fields; category drafts remain distinct.
2. Preset sizes, multiple colours, arbitrary red shade naming, quantities, photo compression and a four-row save.
3. Parent sees one product, chooses M Blue, requests it, and staff approval reduces only that option's availability.
4. Student sees the same grouped options and can enlarge the selected photo; Escape closes the preview.
5. Editing preserves existing option stock/photo; adding L Red extends the original grouped product.
6. Book creation produces format/edition options without colour controls.
7. Studio and shop fit a 360px viewport; light/dark screenshots were inspected and colour control contrast corrected.

## Regression and installation

The 19 existing store workflow checks passed, covering independent purchasing approvals, receipts, reservation/invoice matching, payment-confirmed collection, full returns, Finance withdrawal, count corrections and access boundaries.

Read-only authenticated regression visited 666 pages across 14 roles with no HTTP/page errors, PHP warnings, fatal/parse errors or undefined-function/method errors. Changed PHP and JavaScript syntax checks passed.

All five existing-updater checks passed: injected mid-install failure recovery, full 32-file installation with manifest/configuration/journal checks, repeated-version refusal, explicit rollback to 5.3.25 and traversal rejection. The studio helpers are embedded in the already approved inventory module so the existing admin updater accepts the ZIP without a manual prerequisite update.

The package manifest and all file hashes were compared with the source used for validation. Synthetic fixture records were cleaned after testing. No secrets, live data, test scripts or local configuration are included in the package.
