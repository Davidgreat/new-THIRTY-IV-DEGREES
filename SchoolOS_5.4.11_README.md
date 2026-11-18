# SchoolOS 5.4.11 — Accessible Partner demo dashboard

Back up matching files, database and keys, then install **SchoolOS_5.4.11_Partner_Demo_Dashboard_Update.zip** through Platform Super Admin → Updates & tools. This is a cumulative 43-file release including 5.4.10 compact pricing/registration and 5.4.9 prorated upgrades.

Open the login page, select **Partner**, then press **Step into your workspace** using the filled fictional credentials. The demo now opens an affiliate dashboard instead of stopping at a financial-actions-disabled notice. The direct `/partner-account` link and partner workspace route also display it.

The preview includes six fictional referral schools, commission/available/held/paid totals, a referral pie chart, monthly commission bars, an example referral link, bank-setup guidance and payout history. **Preview payout request** locally illustrates reserving a selected sample amount; reload resets the example. It never submits or stores a withdrawal.

The display is intentionally independent of live affiliate settings and missing affiliate tables in older sandboxes. Existing configured demo accounts work without resetting the sandbox, installing affiliate tables, changing credentials or touching real school records. The Partner demo still requires the platform’s normal isolated demo configuration and valid demo sign-in.

All displayed figures are clearly labelled fictional examples, not earned money. No real bank details are collected. The sample referral link uses a non-routable `.invalid` domain and cannot attribute a real school. Live affiliate applications, account/bank changes, payout requests, transfers and provider calls remain blocked in demo mode. Actual approved partner accounts retain the existing live dashboard and financial controls. Public JS/CSS asset versions are refreshed so existing browsers load the new preview behavior.

Validation: actual Partner demo login against a separately provisioned fictional sandbox; workspace and direct clean-link access; local payout preview/reset; desktop and phone light/dark layouts; no external provider requests or browser errors; attempts to invoke financial actions denied; no affiliate schema/financial writes; live/non-partner preview access denied; name escaping; PHP syntax checks; updater install/hash and rollback/recovery scenarios. No real financial transaction, email or hosted installation was performed.
