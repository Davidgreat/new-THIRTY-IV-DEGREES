> A newer cumulative release and refreshed manual are available: [SchoolOS 5.4.3 — Launch audit and current guides](SchoolOS_5.4.3_README.md).

# SchoolOS 5.4.2 — A calmer school start, connected leadership

This cumulative update retains the modular roles and connected workflows from 5.4.1. It reorganises the School Admin home around three clear places and extends the Principal workspace with scoped financial reports and reviewed chat drafts.

## Install and open

1. Keep a database backup. Upload `SchoolOS_5.4.2_Calm_Admin_and_Principal_Followups_Update.zip` unchanged through the real Platform Super Admin updater.
2. Sign in as School Admin. Open **Start my school**. Schools with incomplete start-up records see the guide by default.
3. Work through one step at a time. Use **My school day** whenever you want daily tools. You can choose it as your default home even while setup is in progress; the remaining progress stays visible. Once all six checks are ready, the daily home becomes the default automatically.
4. Open **More tools** to search the full school toolkit. Existing pages and record links remain available; optional jobs and services are still selected in Roles & permissions.

No configuration file, database credentials, encryption keys, synthetic records or new unapproved runtime filenames are included. Installation does not replace school records or create unnecessary staff accounts. This package was tested locally, not installed on your hosted site.

## A focused starting guide

| Step | What makes it ready |
|---|---|
| Your school | School name, address, phone and email; installed workspace tables available |
| Your classes | Classes and subjects exist; each class has a school session |
| Your teaching team | Active school staff have current employment links; teachers have valid current-session allocations |
| Safe access | The School Admin explicitly records the start-up access plan |
| Your pupils | Pupil records exist and have valid classes |
| Connect families | Pupils have verified active parent access; active family logins have verified pupil links |

The percentage counts these six saved-record checks. It is not certification that every service is configured or that the records are correct. Existing data is recognised; nobody needs to recreate a family or teacher. The access-plan acknowledgement does not approve a formal privacy register or certify legal compliance.

Fees, assessment rules, calendar, email delivery and extra services appear under **What can wait?** Configure a service before using it. For example, validate assessment and report settings before publishing results, and test email delivery before relying on login emails. The full privacy and retention review remains in Reports & privacy policies.

The school-details form preserves existing colours, logo and motto. Advanced record matching in the staff form stays available under **Already have a staff record?** to avoid duplicate employee records. First-day setup does not force a school to activate all staff roles.

## Guidance and daily work

The guide shows one active step, a compact step list and a clear next action. **Listen to this step** uses the browser/device speech facility, starts only on request and has a Stop control. It reads generic step guidance, not pupil names, balances or credentials. Available voices and sound depend on the browser and device; the same guidance always remains on screen.

The daily home contains real pupil, team and class counts, common actions, a short attention queue and a fee summary. Notifications remain compact and expandable. The optional walkthrough now explains the three-part layout. Mobile and light/dark themes retain the platform's glass appearance with quieter foreground presentation.

## Principal access

Principals open a leadership overview with separate pupil, fee and academic areas. Existing attendance charts, assigned teachers, published-result status and academic action notes remain connected. New fee reports show current invoices, balances, owing pupils, class/name filters, pagination and an explicitly permitted CSV export. Billed/collected/outstanding values use the shared Finance invoice records; invoice allocations are not a bank balance or profit statement.

School-wide leadership finance grants additionally see an expandable summary of confirmed collections, paid supplier expenses, paid refunds and recorded net movement. Class- and branch-scoped grants cannot see this school-wide total. Opening balances and costs outside the Finance ledger are excluded.

New Principal templates include:

- `principal_finance.view` — fee reports within the assignment's existing scope.
- `principal_finance.export` — CSV export, intersected with view scope.
- `principal_followup.create` — prepare a reviewed parent or teaching-colleague chat draft.
- `family_contact.view` — permitted verified-parent conversations, already included in the earlier standard template.

Existing real-school roles are **not silently expanded**. School Admin → More tools → Principal financial reports offers a reviewed action for existing academic-leadership roles. It retains all existing scope and other permissions, checks the role version and records the change. Alternatively edit individual permissions under Roles & permissions. A role change affects everyone assigned that role; review it before confirming.

These permissions do not grant payment reconciliation, spending/refund approval, payroll, subscription changes or school-owner authority. Optional module switches, individual blocks, class/branch scopes and verified contacts still apply. Custom staff permissions cannot grant School Admin identity.

## Follow-ups that stay in school chat

Fee reminders, pupil attendance checks, learning follow-ups, teacher-support checks, staff setup checks and family login-help drafts open the existing in-app chat composer. Review/edit and explicitly press Send. Preparing or opening a draft never inserts a chat message.

Parent messages require a current verified child link and permitted chat contact. Teaching-colleague messages require a current teaching allocation within the Principal's academic and follow-up scopes. Inactive/unrelated contacts are refused. An unmarked register is described as a check, not an accusation of absence.

Draft URLs carry an opaque, session-bound token rather than message text. Tokens expire after ten minutes, are limited to ten per session and are bound to the actor, school and intended recipient. Opening the composer rechecks access, relationship and current balance. Paid/cancelled invoices, revoked relationships, another actor or a changed group-chat target cannot reveal the saved draft. The final composer remains editable; normal chat permissions are also enforced on explicit Send.

Find these actions in Principal → Fees & follow-ups / Pupils & follow-ups / Teaching & academic actions; School Admin → Fees overview links to balances and in-app follow-ups. Parent account cards include family login help; staff account details include staff setup help. No automatic WhatsApp, email or chat sending was introduced.

## Existing demos and recovery

All 41 demo picker logins were checked. Marked isolated demos upgrade additively. Only the exact old fixed demo Principal template receives the new standard demo permissions; passwords and account IDs remain unchanged. Real-school role permissions are not changed by this sandbox upgrade.

The existing updater's access-aware rollback guard is unchanged. File rollback from 5.4.2 to 5.4.1 was tested with modular records present. Older incompatible file-only downgrades remain refused after modular adoption. File rollback does not reverse records or permission changes; recovery of data needs the matching database backup.

See [validation](SchoolOS_5.4.2_Validation.md), [workflow map](SchoolOS_5.4.2_Workflow_Map.md) and the matching SHA256SUMS file.
