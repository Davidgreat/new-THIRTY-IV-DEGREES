# SchoolOS 5.4.2 validation

Validated locally with synthetic MariaDB tenants, a marked isolated demo, real HTTP requests and Chromium. No production database access, hosted deployment, live email delivery, WhatsApp send or real payment occurred.

## Functional and access checks

- Six truthful startup checks from school records; optional services excluded; empty school remains incomplete and saved class data changes progress.
- Owner-only setup changes and CSRF rejection. Actual HTTP school-details save and explicit daily-home preference. Saved branding colours/motto retained.
- Principal templates include separate fee view/export and draft actions, without payment approval. Existing custom roles are not auto-expanded. Explicit owner-reviewed upgrade preserves assigned class scope and checks stale versions.
- Canonical fee totals, class isolation, unrelated-parent refusal and immediate financial-module revocation.
- Session-bound draft actor/recipient/expiry checks; no message inserted by draft preparation. Paid/cancelled invoices and removed parent links rejected on recheck. Group-chat substitution refused.
- Unmarked attendance wording stays distinct from absent. Teaching colleague drafts require an allocation within leadership scope; administrative staff-setup drafts remain owner-only.
- Actual explicit chat Send persists in the existing message table. CSV export applies view/export scope intersection and escapes formula-leading text. Class-scoped leaders cannot read school-wide cash movement.

## Browser checks

- School Admin guide, six step views, daily home and tools at 360px/1440px in light/dark themes; document width checked and representative screenshots inspected.
- More tools search and existing school routes, including students, parents, teachers, team, record links, academics, attendance, results, fees, announcements, services, operations, intelligence, settings, roles, staff work, audit and family pages.
- Principal overview/fees/pupils/academic panels at phone and desktop widths; unrelated class pupils absent.
- Fee-reminder form opens editable private chat with a draft-ready notice; URL contains no message body; explicit Send works.
- Voice starts only after clicking, reads the generic step text and stops on request. Speech API was mocked for deterministic validation; audible device output was not claimed.
- No JavaScript page errors in the main dashboard checks.
- All 41 isolated demo logins reach their dashboards. An old fixed Principal sandbox template upgrades without changing account IDs or passwords.

## Package and recovery checks

- 44 PHP/JavaScript syntax checks pass.
- Cumulative 41-file approved-destination package, manifest SHA-256 hashes and unchanged configuration after installation.
- Existing 5.4.1 updater installs 5.4.2; injected mid-install failure restores changed files; same-version install is refused; unsafe traversal ZIP is refused.
- Explicit file rollback restores original 5.4.1 files and metadata while modular access records exist. The access-aware downgrade guard was not changed.

Existing custom-role financial access requires a School Admin's explicit review. A saved access plan is not legal/privacy certification. Browser voices depend on the user's device. Finance displays recorded values and clearly distinguishes invoice collections/net movement from bank balance or profit. Scope checks do not imply live bank or external service verification.
