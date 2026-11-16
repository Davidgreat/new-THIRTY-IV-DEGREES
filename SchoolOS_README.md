# School OS 5.3.35 — School-led admissions and family access

[Open the installable ZIP on GitHub](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.35_School_Led_Admissions_Update.zip)

Admissions can now register pupils directly at the school office, record the school's admission decision and prepare the right family accounts. A public application, entrance test or fabricated offer is not required for an office admission.

## What changes

- **Register a pupil** is the main admissions action. Save/edit a draft, select a class/session, verify a new or existing guardian, review possible duplicates and confirm admission.
- Phone-first family records work without email. A pupil record, guardian relationship and login remain distinct and clearly labeled.
- Admission creates the pupil, admission number, class placement, student details, guardian relationship and activity history together. Retry protection prevents the same registration from creating a second pupil.
- Optional private document uploads support review and replacement history. Pending/rejected uploads block admission; verified copies carry into Student Records.
- **Family & login setup** covers new and existing pupils. Search existing guardians and parent/student logins, add a second authorized guardian, prepare access requests and see each pupil's connection checklist.
- One verified parent account can cover siblings without changing its password. An optional student account connects to exactly one pupil.
- School administrators approve access by default. A school administrator can explicitly delegate reviewed parent/student account approval to admissions; this does not grant administrative roles.
- New accounts receive school sign-in IDs, a one-time printable handover and a temporary password valid for 72 hours. A new personal password is required before opening school records. Existing email sign-in continues to work.
- The separate generic school staff-account route now also uses temporary credentials and a first-login password change. Parent/student creation and raw numeric family linking point into the verified pupil-led flow.
- CSV imports produce reviewable drafts, up to 100 pupils per file, without activating accounts or creating invoices. A template and school class-code reference are included.
- The overview includes a family-access donut, registration counts and pending approvals. Existing applications, offers, tests, reminders and public-form settings remain in **More admission tools**.
- Linked office-admission parents can chat with admissions and their linked children. School/role/child restrictions remain enforced.
- A shared routing fix keeps dashboard pagination inside the dashboard rather than opening the public website.

The existing personal welcome, glass surfaces, light/dark themes, mobile layouts and automatic animated circles remain included.

## Install and prepare

1. Back up the application files **and database**.
2. Open the ZIP link above and choose **Download raw file**.
3. Install through **Platform Super Admin → Core updates** using the existing updater.
4. Sign in as the **school administrator**, open **Admissions → Pupil registrations**, and click **Prepare pupil registration** if shown. This additive preparation creates the new registration/access tables and prepares the existing Student Records/Experience dependencies. It keeps existing records.
5. Admissions can then use **Register a pupil**. After confirming admission, open **Family & login setup**. The administrator reviews pending access requests there and privately hands over newly issued credentials.
6. Refresh already-open dashboard tabs so the versioned CSS/JavaScript reloads.

Schools sharing the same database need the table preparation once. Account-approval delegation and family records remain school-specific. A separately configured isolated demo database needs its own preparation; newly built demo databases include the new tables. Its existing safety rules still disable uploads and live providers.

## School sign-in IDs

Examples of formats, not real credentials:

- Parent: `P-<school ID>-<account ID>`
- Student: `S-<school ID>-<account ID>`
- Teacher: `T-<school ID>-<account ID>`
- Staff: `E-<school ID>-<account ID>`
- Admissions: `A-<school ID>-<account ID>`

IDs identify the account; a correct password is still required. For accounts without email, the legacy required email column holds a non-deliverable internal storage key. It is not a contact address, is not handed over as an email and is not automatically verified for external delivery. No email/SMS delivery is claimed or performed by this registration flow.

## Scope and recovery

Existing pupils, accounts, passwords and application histories are not silently relinked or reset. Review existing pupils through **Family & login setup** and verify relationships before adding access. Existing public-application settings are preserved; public forms are optional, and new school form settings remain closed by default.

Finance invoices, actual payment confirmation and optional transport/boarding assignments remain the responsibility of their school teams. Registration does not invent payments, charge optional services or automatically allocate a bus/bed.

The ZIP contains 36 approved application files plus `release.json`, without configuration, credentials or fixtures. Database preparation is additive. File rollback does not remove new pupil/family records or tables. School-ID-only accounts require this version's authentication support; if rolling back, plan access recovery or restore the corresponding database backup rather than assuming the old login screen supports the new IDs.

[Workflow and role guide](SchoolOS_5.3.35_Admissions_Workflow.md) · [Validation](SchoolOS_5.3.35_Validation.md) · [ZIP checksum](SchoolOS_5.3.35_SHA256SUMS.txt)

Validated locally with fictional records. This release has not been installed or tested against the hosted school's production database in this session.
