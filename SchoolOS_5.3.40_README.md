# SchoolOS 5.3.40 — Demo login recovery

Cumulative update, including all 5.3.39 dashboards, demo choices and branded family registration improvements.

## Install

1. Download `SchoolOS_5.3.40_Demo_Login_Recovery_Update.zip` using GitHub's Download raw file button.
2. Sign in with your real Platform Super Admin account and install the ZIP through the platform updater. Keep the updater backup.
3. Sign out and select a demo role again. Existing valid sandbox accounts no longer depend on completing optional sample-data generation.
4. If a demo still reports a reference code, sign in with your real Platform Super Admin account. In **Setup & account → Demo health & account preparation**, choose **Check sandbox connection & accounts**. Use **Prepare demo workspaces & missing accounts** if workspace preparation is needed. This action preserves existing records and passwords; it does not rebuild the sandbox.

Do not use **Replace fictional demo data** for this repair: that separate operation clears visitor changes. Do not enter live school database credentials in the demo configuration.

## What changed

5.3.39 ran the full illustrative-data upgrade before every unprepared demo login. A conflict in visitor-edited HR data, or an unbuildable example timetable, could abort that shared upgrade and prevent every demo role from signing in. A synthetic sandbox with an ended employment record reproduced this failure. The exact cause on a hosted installation requires its private diagnostic.

5.3.40 prepares missing fixed-role demo accounts and permissions separately, retains valid existing credentials, records account-specific HR conflicts for review, and keeps optional purchases, timetable and support examples out of the login upgrade. Optional preparation errors cannot block existing valid accounts. Core connection and ownership failures still stop sign-in.

The real Platform Super Admin gains read-only connection/account checks, additive workspace preparation and an escaped, credential-redacted private diagnostic. Public errors provide safe reference codes instead of database details.

## References

- D01: missing isolated database configuration or active maintenance flag.
- D02: isolated database connection unavailable.
- D03: sandbox ownership marker cannot be verified.
- D04: core portal workspace upgrade needs platform preparation.
- D05: demo sign-in failed; inspect the selected account and private diagnostic.
- D06: optional role preparation warning, visible privately; existing valid logins may continue.

No hosted deployment was performed. Install this package through your existing updater. See the validation document and SHA256 file alongside the ZIP.
