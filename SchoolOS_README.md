# SchoolOS 5.4.4 — Clean platform addresses

Cumulative 43-file update. Install the ZIP unchanged through the real Platform Super Admin updater after backing up. It retains the existing modular permissions, school workflows and launch-audit fixes.

## Enable once for the platform

1. Install `SchoolOS_5.4.4_Clean_URLs_Update.zip` through Updates & Plugins.
2. In the real Platform Super Admin account, open **Updates & Plugins → Clean, shareable platform links**.
3. Select **Check server & enable clean links**. A same-origin browser request must reach a dedicated clean path and pass server-side identity/CSRF/nonce checks before activation.
4. Browse the school, sign in, open family registration and check the services your schools use.

Examples after activation: `/login`, `/dashboard`, `/admissions/families`, `/chat`, `/guides/owner`, `/join-family/<private-token>`. An installation in `/campus/` retains that prefix. Filters may still use query parameters. API requests, provider callbacks, signed links and file endpoints retain their existing request behaviour. Existing `index.php?...` navigation links redirect to the matching clean address.

If the check fails, links stay in legacy mode. Apache/LiteSpeed needs the existing front-controller rewrite with mod_rewrite/AllowOverride enabled; Nginx needs equivalent routing configured by the host. This update does not edit server configuration or replace private-file denial rules. It cannot independently certify your production host.

## Recovery

If routing stops working after a hosting change, open `https://YOUR-INSTALLATION/index.php?s=system&legacy_urls=1`, sign in as the real Platform Super Admin and choose **Restore legacy link generation**. Include the installation subfolder where applicable. Do not delete private settings or weaken hosting security. The original physical entry point remains available.

The setting is stored privately in `storage/system/clean-urls.json`, bound to the verified installation base. No database migration, role change, provider configuration change or account re-creation is required. No private configuration, credentials, encryption keys, synthetic records or test utilities are included. The 5.4.1 access-aware downgrade guard remains unchanged.

## Validation

- 263 router/HTML/link checks; 68 HTTP checks for root/subfolder, activation, recovery, scope, callback and path handling.
- 438 authenticated navigation requests across all 41 fictional demo identities: zero server-error findings.
- Browser activation, nested API requests, styles, mobile layout and script errors checked; all 47 current guide/PDF pairs pass.
- 39 PHP files and both changed JavaScript files pass syntax checks.
- The existing 5.4.3 updater installs matching hashes without modifying configuration; interrupted install, explicit rollback, repeated version and traversal scenarios pass.

These are local tests using an isolated fictional database and a PHP front-controller test router. The feature's real-host probe is required; local results are not proof of Apache/Nginx configuration, payment settlement, SMTP delivery, live media capacity or production load. The prior launch-audit live acceptance requirements still apply.

Previous launch audit and complete guide refresh: [SchoolOS 5.4.3](SchoolOS_5.4.3_README.md).
