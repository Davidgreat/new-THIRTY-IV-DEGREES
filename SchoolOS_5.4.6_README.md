# SchoolOS 5.4.6 — Partner setup routing correction

This cumulative 43-file release fixes a 5.4.5 dispatcher regression: the platform/partner home handler intercepted signed-in requests without an explicit dashboard section before public pages or affiliate handlers could run. As a result, Open programme setup returned the platform overview, signed-in guides could return home, and bank-directory requests could return dashboard HTML.

The dashboard handler now leaves explicit website/guide/private-link routes, affiliate form submissions and recognised service endpoints to their existing dispatchers. Platform staff remain behind the restricted assignment guard; this correction does not grant them affiliate administration or bank access. Existing endpoint authentication, CSRF and approval/provider checks remain.

## Install and continue

1. Back up, then upload SchoolOS_5.4.6_Partner_Setup_Routing_Fix_Update.zip unchanged through Updates & tools.
2. Confirm installed version 5.4.6.
3. Open Partners → Open programme setup. If the programme is not installed, choose Install Website & Affiliates module.
4. Review the percentage, holding period, minimum withdrawal and contact settings. The programme stays disabled until deliberately enabled. Bank verification and payouts still require a working provider configuration.

Existing settings, accounts, records and clean-URL mode are preserved. No new database migration is introduced by this correction. The 5.4.5 support/permissions/downgrade safeguards remain. Existing 5.4.5 operator and partner guidance still applies; built-in guide release labels are updated.

Validation: 42 HTTP routing/installation checks covering root and subfolder clean URLs, actual setup links, fresh programme installation, settings submission, signed-in operator/partner guides, JSON bank endpoint errors, missing-CSRF refusal, platform-staff restrictions and recovery. Browser checks exercise the actual setup click and signed-in guide. The existing updater installs the package with matching hashes and passes interruption/rollback/repeat/traversal scenarios. No real transfer, bank verification or email send was made. Tested locally using isolated fictional records; the package is published for installation, not deployed to the live site.
