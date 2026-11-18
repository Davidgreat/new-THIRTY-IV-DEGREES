# SchoolOS 5.4.8 — One-month free trial on Pricing

Back up and install the cumulative 43-file ZIP through Platform Super Admin → Updates & tools. Then open Pricing. A separate **1-month free trial** card appears alongside the existing paid packages.

The card states the continuation package and price, carries the trial choice into registration and grants one calendar month of real school access. No payment is taken automatically. Month-end dates clamp to the next month’s last valid day (including leap years). The trial expiry is shown in the account and sign-up notice. After expiry, the existing subscription gate requires a verified paid continuation. Paying early retains the remaining trial period in the subscription expiry calculation.

Paid-package choices remain payment first with no trial. Existing subscriptions and the ordinary legacy trial settings are not changed. The separate public trial is intentional even if the older general trial policy is payment-first. Trial intent, continuation package, cycle and quoted price are bound to the registration session; hidden fields cannot convert a paid-bound submission into a trial. Existing account-email uniqueness, registration CSRF, rate limits and payment verification remain.

The trial uses the first active paid monthly package; if none is available, it falls back to an offered paid termly/annual cycle. Its name and price are shown before registration. Active free packages stay separate. If registration is closed or there is no paid continuation package, the card offers contact instead of creating an unusable school. Provider-dependent services retain their normal setup, permission, credit and capacity requirements; a trial does not create provider credits.

Validation uses isolated fictional records: eight trial scenarios (including expiry/month-end/leap-year and paid-intent tampering), all twelve paid-pricing regressions, desktop/phone light/dark browser selection, real browser registration opening school setup, syntax checks and updater/recovery scenarios. No real payment, email or hosted deployment was performed. The ZIP does not include credentials, private configuration, keys or test fixtures, and introduces no database schema migration.

The cumulative package includes [the playful website and public pricing from 5.4.7](SchoolOS_5.4.7_README.md). The separate trial option above supersedes that release’s paid-only pricing entry list.
