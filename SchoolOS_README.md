# SchoolOS 5.4.7 — Playful website and public pricing

Cumulative 43-file release. Back up and install the original ZIP through the real Platform Super Admin updater. Existing records, provider settings, private keys and clean-link mode are preserved. This release does not introduce a database schema migration.

## Website, with a little life

The public SchoolOS pages now have moving translucent circles, soft colour changes and elastic collisions using the proven dashboard motion engine. Buttons and navigation gain a visible hover lift/glow; keyboard focus and phone tap feedback stay usable. The circles cannot intercept input. The engine pauses for hidden/print views and honours the existing accessibility behaviour, including the desktop automatic-motion fallback. Affiliate pages bind only one scene driver even though they also load dashboard controls. Light/dark and mobile layouts retain readable text and prices.

## Public pricing

Open `/pricing` after clean links are enabled, or `index.php?page=pricing`. Pricing appears in navigation/footer and the public website’s start buttons lead there. Monthly, termly (four months) and annual prices come from the active `saas_plans` records. Names, amounts and saved pupil/staff capacities are not invented or copied from the test fixture. Zero-price cycles on a paid package are not offered; an all-zero configured package is presented as free. Inactive packages are hidden. If no plans are ready, the page invites contact instead of inventing prices. Closed registrations display an honest contact path.

The page describes shared SchoolOS capabilities and the need to activate school services/permissions. It does not invent tier-specific feature gates, promise unlimited provider capacity or include third-party credits. External messaging, payments, AI and classroom providers still need their configured services and live acceptance.

Before launch, sign in as Platform Super Admin → Plans & billing tools → Public pricing packages. Review names, prices, capacities and active availability. The editor checks role, CSRF, amounts and a concurrent-change stamp. Saved school enrolment amounts are retained; use the existing subscription controls for existing schools. New packages can still be created through the existing plan-creation form.

## Choose a package → create a school → pay

A pricing choice opens registration with the package and billing cycle preselected. Those fields are locked, with a Change package link. The server stores the package, cycle, price snapshot and registration key in the session; it does not trust a client-supplied trial flag or amount.

Pricing-origin registrations have zero trial days even when the plan’s ordinary trial setting is positive. A paid school is created as pending, behind the existing subscription/payment gate, until the provider verifies the exact charge, reference and NGN currency. Choosing a package or a browser return never proves payment. A configured free package is active as a free subscription, not a timed trial. There is no automatic renewal debit.

Removing pricing fields cannot turn that selected registration into a trial. Altered package/cycle, inactive plans, unavailable cycles, malformed selections or a changed quoted price are refused before school creation. The ordinary trial policy of separate legacy registration routes is preserved; existing school subscriptions are not retroactively changed.

## Validation and boundaries

Checks use a separate ownership-marked fictional database, PHP 8.4, MariaDB and Chromium. They cover server-bound pricing selection, no-trial state, price/plan/cycle tampering, free and legacy-trial paths, exact-cycle activation with mocked verified payment, root/subfolder clean links, actual browser package selection, no-JavaScript locked controls, desktop/phone light/dark layouts, visible motion, hover glow, signed-in operator editing, all current guide/PDF endpoints and update/recovery scenarios. The test fixtures and their invented prices are not shipped.

No real payment, provider charge, customer email or hosted deployment was performed. Publish the prices you actually intend to offer, verify your live payment/provider path and retain the previous launch acceptance checklist. This package is published for installation; installing it on the live host is still required.

Previous releases: [5.4.6 routing correction](SchoolOS_5.4.6_README.md) · [5.4.5 platform workspace](SchoolOS_5.4.5_README.md).
