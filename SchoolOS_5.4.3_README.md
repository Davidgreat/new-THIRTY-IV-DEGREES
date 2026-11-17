# SchoolOS 5.4.3 — Launch audit and current user guides

Cumulative 43-file core update, including 5.4.2 and earlier work. Install the ZIP unchanged through the real Platform Super Admin updater after backing up.

This release fixes two reproducible mixed-collation failures affecting parent homework and class-targeted communications, removes dead operations links from specialist personal-employment pages, implements the previously empty Platform Reports page, and hardens notice-tenant and guide-input checks. It adds an operator-only launch-facts panel that clearly distinguishes detected facts from unverified live acceptance.

The complete guide refresh includes 47 searchable entries covering all 35 staff job profiles, owners, platform operators, families and partners. The full manual has 200 sections. Web guides support role/task filters, text search, print, PDF and offline HTML. Existing guide URLs remain available. Individual job guides explain concrete steps, permission boundaries and external-service dependencies.

After installation:

1. Open **Help / Guides → Start here** for the first school-day flow.
2. Open **Platform → Reports** for real aggregate school/account/subscription records.
3. Open **Updates & Plugins → Before your first live school** and complete the applicable live acceptance checks.
4. Read `SchoolOS_5.4.3_Production_Readiness_Audit.md` before public launch. The recommendation is a supervised pilot after installation and live-host sign-off, not unconditional production certification.

Fresh validation includes 284 focused checks, all 41 demo identity logins in a 1,284-request navigation sweep, a 244-request affected-role recheck with zero findings, all 47 guide/PDF pairs, mobile/desktop light/dark browser checks, 44 syntax checks and update/recovery/rollback scenarios. See the audit and evidence summary for scope and limitations.

The release contains no config.php, credentials, encryption keys, production records or test utilities. No database schema migration is required for these fixes. Existing configuration and records are preserved. The access-aware downgrade guard remains; file rollback does not undo database or permission changes.

The live site could not be independently validated from this audit network. Backups/restore, private-path protection, real provider delivery/payments/media and target-load capacity need operator acceptance before being relied on. Optional services can remain disabled while core school functions launch.
