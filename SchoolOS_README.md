# School OS 5.3.36 — Existing-school family onboarding

[Open the installable ZIP on GitHub](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.36_Family_Onboarding_Update.zip)

Schools can onboard existing families through one reviewed form. Staff can enter a family at the office, or share the school's unique parent-registration link. Submission alone never grants access.

## Included

- Admissions → Family onboarding: school links, staff-assisted entry, parent/child review and account handover.
- A parent form with email, WhatsApp number and up to 10 children, with name, birth date, class/arm, admission number if known and optional student access.
- Staff search/match existing pupils to preserve their history, or confirm a missing school record. Matches never automatically grant access.
- Admissions prepares verified matches. School administrators approve by default; existing explicit delegation of reviewed family-account approval also applies.
- Approve reviewed siblings together, approve individually or return one child for correction while others move forward.
- One parent account covers siblings. Existing parent/student passwords stay unchanged.
- New accounts receive school sign-in IDs, the login URL and single-use password-setup links valid for 72 hours. Plaintext passwords are not emailed or put in WhatsApp.
- Automatic email attempt after approval through the configured SchoolOS platform SMTP, or an explicitly selected school SMTP service. Failure does not undo enrollment.
- Delivery states distinguish queued, sending, SMTP accepted, failed and uncertain outcomes. Retry controls preserve accounts and personal passwords.
- Open WhatsApp handover opens the supplied number with prepared instructions; staff review/send it themselves. Opening is not proof of sending or delivery.
- Private parent return links support progress and corrections. Verified staff can replace a lost link and revoke its older copy.
- Responsive glass panels, a progress donut, searchable records, school-scoped review notifications and an activity trail.

Existing pupil records, applications/offers, personal welcomes and animated backgrounds remain included. Staff who are also parents can receive a separate parent school-ID account without changing their staff login.

## Install and configure

1. Back up application files, database and private encryption keys.
2. Open the ZIP above, choose Download raw file, then install through Platform Super Admin → Core updates.
3. As school administrator, open Admissions → Family onboarding and click Prepare family onboarding if shown. Preparation adds tables without deleting existing school records.
4. Ensure Platform Super Admin → Setup & account has the correct canonical HTTPS installation address. Include any installation subdirectory, without /index.php. Emailed links use this trusted address, not request headers.
5. Open Share school link & email settings. Enable family forms and generate the school link. Admissions may copy/share it; the school administrator controls availability and replacement.
6. Choose SchoolOS platform SMTP or This school's SMTP. Platform mode uses Platform Super Admin → Integrations → SMTP Email Configuration. School mode uses its own verified sender, host, port, TLS options and credentials.
7. Test with fictional records and an inbox controlled by the school before sharing the link widely.

School SMTP supports public provider hosts on 465, 587 or 2525 with SSL/TLS or STARTTLS. The trusted platform configuration retains its existing port policy. Credentials are encrypted and never redisplayed; blank school fields preserve saved values. A selected school SMTP failure is reported rather than silently switching sender. These school settings apply to family handovers, not other modules' provider settings.

## Day-to-day flow

Share link or enter family → parent adds children → school matches and verifies → authorized approval → accounts connected → email/WhatsApp handover → personal password setup → sign in.

Use existing pupil records whenever available. Parent-entered details do not overwrite existing classes, fees, results or history. Verify guardian authority and ownership of email/WhatsApp contacts before approval. A matching name alone is not verification.

An inactive pending parent request may be explicitly verified and approved; a deliberately disabled account is not silently reactivated. If an email belongs to a staff/other-school account, a separate verified parent account can use a school ID while that original login remains unchanged.

## Queued-mail worker

Approval attempts email after the school-record transaction commits. An optional hosting cron can process remaining queued handovers:

```sh
php /absolute/path/public_html/services_worker.php --family-onboarding --tenant=1 --limit=20
```

Use the actual school tenant ID. Failed/uncertain sends require staff review before retry; interrupted sends are not blindly repeated. SMTP acceptance does not confirm inbox delivery. Real deliverability depends on the configured mail service and sender/domain setup.

## Data and rollback

The cumulative ZIP contains 36 approved application files plus release.json. Configuration, private keys, mail credentials and test data are excluded. Seven additive tables store links, family requests, child reviews, protected setup tokens, encrypted delivery bodies, events and school SMTP settings. Shared databases need preparation once; records and settings remain school-scoped.

This form does not import historical results/attendance/opening balances or invent a payment, invoice, bus or boarding assignment. Existing pupils connect by their existing IDs.

File rollback does not roll back database records or passwords. The new forms and setup URLs require this version. Existing school-ID sign-in remains supported by 5.3.35 once a personal password is set; plan recovery before reverting.

Shared demo mode allows fictional office-assisted review, while public family links, SMTP changes, external email and WhatsApp handovers remain disabled.

[Workflow guide](SchoolOS_5.3.36_Family_Onboarding_Guide.md) · [Validation](SchoolOS_5.3.36_Validation.md) · [Checksum](SchoolOS_5.3.36_SHA256SUMS.txt)

Tested locally. This session did not deploy to the hosted school or use its real SMTP account.
