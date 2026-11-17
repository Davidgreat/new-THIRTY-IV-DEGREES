# SchoolOS 5.3.40 validation

Local synthetic MariaDB sandbox and Chromium testing; no production database access or hosted deployment.

- Reproduced 5.3.39's mandatory sample-data upgrade failure using an existing exited HR record.
- Migrated a synthetic fourteen-account sandbox to all thirty-five demo identities through the actual shared connection path. Preserved existing password hashes and exited employment history.
- Checked all thirty-five picker credentials against the marked sandbox.
- Forced optional account preparation to fail; existing sandbox connection remained usable and a private D06 diagnostic was recorded.
- Refused an incorrect ownership marker with safe public D03 messaging and refused account preparation on the ordinary database.
- Forced core workspace review (D04), then confirmed explicit additive preparation restored access.
- Preserved a changed demo password during preparation and flagged the picker credential for administrator review.
- Exercised real Platform Super Admin login, CSRF-protected health check and additive preparation through HTTP.
- Refused private diagnostics and preparation for an ordinary School Admin.
- Verified configured credential redaction and HTML escaping in private diagnostics.
- Linted all forty-two application PHP files.
- Tested original updater installation, every manifest hash, unchanged configuration, injected-failure rollback, repeated-version refusal, explicit rollback and traversal refusal.

The accompanying browser result covers all thirty-five isolated demo picker logins and dashboard rendering. This hotfix changes the shared login and platform diagnostic paths; the existing 5.3.39 workflow audit remains available for the unchanged role modules.

Hosted database configuration remains installation-specific. The new diagnostic identifies a connection, ownership, core preparation or credential problem if the shared-upgrade repair is not sufficient.
