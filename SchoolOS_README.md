# SchoolOS 5.4.12 — Partner sign-out and public homepage

Back up matching files/database/private keys, then install **SchoolOS_5.4.12_Partner_Logout_Homepage_Update.zip** through Platform Super Admin → Updates & tools. This is a cumulative 43-file package including 5.4.11 Partner demo and earlier releases. No schema migration or sandbox reset is required.

The affiliate demo could remain visible because a signed-in partner visiting the bare public root was dispatched as if it had requested its workspace. The public affiliate header also lacked a clear sign-out control.

The signed-in public/partner header now offers **My workspace** and **Sign out**. A partner visiting the bare homepage (including common marketing tracking parameters) gets the public website. Its explicit workspace and partner-account links still open the affiliate dashboard. Other roles retain their existing default workspace routing.

Sign out destroys the active server session, expires its authentication cookie and clears the demo selector, then redirects to the public homepage. The homepage offers Log in. This ends the active session; it does not revoke other independently signed-in devices. Authenticated public/partner pages restored from browser history reload to check current authentication instead of retaining an old dashboard snapshot. Public JS asset versions are updated.

Validation uses owned isolated fictional databases and a separately provisioned demo sandbox: actual Partner demo sign-in, signed-in root/homepage and tracking-link navigation, explicit workspace access, visible sign-out, guest homepage after logout, expired demo cookies, rejected replay of the old demo session cookie and browser Back. Each scenario ran with legacy and clean links at domain-root and /campus/ installations. Normal partner logout and an explicit restored-history event were also tested. All browser checks, PHP syntax checks, installer/hash verification, injected failure recovery, repeated-install rejection and rollback passed. No real school account, provider payment or hosted installation was changed.

After installing, reload the partner page, choose Sign out and open the homepage. Existing demo credentials and fictional records are retained. The Partner demo still displays its read-only fictional financial preview, with live banking and transfers disabled.

Earlier cumulative releases: [5.4.11 Partner demo](SchoolOS_5.4.11_README.md) · [5.4.10 compact pricing & registration](SchoolOS_5.4.10_README.md).
