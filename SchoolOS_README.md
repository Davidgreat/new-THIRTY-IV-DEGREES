# SchoolOS 5.4.5 — Platform command centre and connected partners

Cumulative 43-file update. Back up the matching database, application/uploads and private keys, then install the original ZIP through the real Platform Super Admin updater. This release retains clean-URL compatibility and all previous school workflows.

## Start after installation

1. Sign in as the real Platform Super Admin and open **Overview**. The new additive platform tables are prepared automatically on first access; the database account needs CREATE TABLE permission.
2. Open **Schools** to search registered schools and filter paid active, free active, trial, expired/inactive, missing-plan and suspended records. Each school is counted once using its enrolment/current subscription.
3. Open **Money** for live subscription receipts, schools with live receipts, recorded outgoings, exact chart figures and CSV export. Test payments and historical records without environment evidence stay separate. The historical evidence check reads the provider; it does not charge a school. Net recorded movement is not a bank balance or profit, and excludes school fee collections.
4. Open **Platform team** to create verified colleagues. Check their permissions and select assigned schools. A shown-once temporary credential expires after 72 hours and requires a personal password. Share it privately. Reissue invalidates existing sessions; school staff accounts remain separate.
5. Use **Helpdesk** for school and billing cases. Assign colleagues, reply to the school, keep private team notes, set status/priority or escalate. Schools see replies in their own support page and in-app notifications. Platform colleagues work only on assigned cases/schools unless triage access is explicitly checked.
6. Use **Team tasks** for work with a named owner, an optional school and a due date. Colleagues record progress notes, complete work or escalate it to the Super Admin.

## School support visits — enter and return

Open Schools, choose the school and use **Enter school support**. A reason and the operator’s current password are required. An active School Admin must exist. A support visit lasts at most 30 minutes, is visible and audited, and returns to the original platform identity. Access changes or expiry end the visit; expired submitted actions are discarded before returning.

Visits are **view only by default**. Platform colleagues with school.visit can visit only assigned schools and cannot edit. The Super Admin may explicitly enable limited academic setup: topics/coverage, allocations, timetable/resources, and saving classes, subjects, curricula, sessions or terms. Private chat, credentials, banking, exports, account/permission changes, grades/publication and financial actions are unavailable. This is deliberately a scoped support workflow, not unrestricted impersonation. The school’s subscription is not changed. The original platform operator is recorded on permitted setup audit events.

## Platform money records

Already-paid expenses and subscription refunds can be recorded by the Super Admin with their actual reference, date, amount and reason. No transfer is initiated. Duplicate references and future dates are refused; refunds require a verified live source and cannot exceed it. Mistaken entries can be voided with password confirmation and a reason; history remains visible, totals exclude them, and no bank movement is reversed. Keep the external receipt. Successful live partner payouts are reported separately.

## Partner workspace

The partner’s ordinary dashboard now opens the connected affiliate workspace. It includes referral conversion and commission charts, holding/available/paid balances, a personal share link, Nigerian bank search and provider account-name verification, withdrawal requests, cancellation of an own unprocessed request, and expandable referral/commission/withdrawal history. Repeated submission of a request form is refused. Test and live records stay separate. A changed bank account never replaces the recipient already saved on a withdrawal.

Programme applications, rates, holding periods, payout reviews and reconciliation remain connected to the existing financial engine. Settings now use percentages and Naira. Payout initiation requires Super Admin password confirmation. Real account resolution and transfers still require working Paystack settings, provider availability/balance and normal provider approval. No live payout, real SMTP send or real bank lookup was performed during local testing.

## A calmer update page

Updates & tools leads with the installed version and trusted release upload. Recovery, clean-link settings, launch/hosting checks, optional declarative packages and private-file protection remain under **Advanced tools & recovery**. They were reorganised, not removed. Update actions redirect to a fresh page to avoid re-submitting an upload on refresh.

## Recovery and access boundaries

The existing modular-access downgrade guard remains. Once platform team/support/task/outgoing records exist, file-only downgrade below 5.4.5 is also refused. A deeper recovery requires the matching database/files/keys backup; do not replace only the old entry point to bypass this guard. No configuration file, production data, credentials, private keys or synthetic fixture utilities are included in this release.

Updated built-in guidance includes the new platform colleague role and the revised partner and operator workflows. The complete manual is provided as HTML, Markdown and printable PDF.

## Validation scope

Local testing uses PHP 8.4, MariaDB and Chromium with an ownership-marked fictional database, separate from the existing database. Results include 1,148 authenticated navigation requests across all 41 demo identities with zero findings, 36 HTTP workflow checks, 68 root/subfolder URL checks, focused permission/finance/affiliate/support tests, mobile/desktop light/dark checks, all 48 guide/PDF pairs, syntax checks and updater/recovery scenarios. See Validation.json for exact suite counts.

These checks do not certify production load, a real host’s routing/security, provider settlement, SMTP arrival or live-class capacity. Continue the existing live acceptance checklist for services you offer. This package is published for installation; it was not deployed to your hosted site from this workspace.

Previous releases: [5.4.4 clean URLs](SchoolOS_5.4.4_README.md) · [5.4.3 launch audit](SchoolOS_5.4.3_README.md).
