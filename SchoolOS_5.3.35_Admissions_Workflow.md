# School OS 5.3.35 — Pupil registration and family account guide

## Who creates pupils?

The school's admissions officer or school administrator registers a pupil inside Admissions. The main route is school-led; families do not need to apply publicly or create their own accounts first.

There are three supported starting points:

1. **School-office registration:** for a new or transferring pupil whose admission is handled by the school. Save a draft, review it and confirm the recorded decision.
2. **Application review:** the existing optional enquiry, assessment, offer and acceptance process remains available under More admission tools. Finish its existing checked enrollment step, then use Family & login setup.
3. **Existing pupils:** search Family & login setup to repair or complete access without registering the child again. CSV import is for records not yet in SchoolOS and creates drafts for individual review.

## What is created, and when?

| Stage | Records/system behavior | Access granted? |
|---|---|---|
| Save a registration | Draft pupil and guardian details, target class and activity entry | No |
| Review optional uploaded documents | Private files and checked review outcomes | No |
| Confirm school-office admission | Pupil, unique admission number, class placement, student details, guardian relationship and timeline; verified documents copied into pupil record | No login is silently issued |
| Prepare family/student access | Explicit account request tied to this pupil and verified guardian or pupil identity | No |
| Authorized approval | Reuse a verified account or create one; connect its dashboard to the correct pupil | Yes, subject to first-password-change gate for new accounts |
| Hand over a new credential | One-time school-ID/temporary-password slip; 72-hour initial expiry | Password change required before school records |

School-office admission does not fabricate an online application, test result, offer, payment or invoice.

## Family setup

A guardian contact is not a portal account. A saved contact does not by itself let someone see a child's data.

Search before creating a contact. When a sibling already attends, select the existing guardian and verify their authority for the new child. A previously approved account for that same guardian can be reused after the new child relationship is approved. A matching name/email alone never grants access.

For existing logins, explicitly search/select the verified account. The password is preserved. Adding a sibling does not issue another parent password. Multiple authorized guardians may be connected independently.

A student login is optional. Issue one when the pupil needs their own learning portal or live-class access. Each student login connects to exactly one pupil. Younger pupils can have only parent access if that is the school's choice.

## Account approval and handover

School administrators approve by default. Under Family & login setup, the administrator can explicitly allow admissions officers to approve only the reviewed parent/student account requests in this flow. The decision is recorded and can be revoked. It does not allow admissions to issue administrator roles.

For a new account, approval generates a random temporary password and school sign-in ID. The handover is shown once, can be printed privately and requires a first-login password change. It expires after 72 hours. No automatic external message is sent. If lost or expired, an administrator uses verified recovery after checking the person and issued school ID or registered email.

For an existing account, approval only adds the verified link and keeps its password. Pending or inactive accounts need administrator review; the system does not silently activate an email match.

## Drafts, duplicate checks and imports

A saved draft can be corrected before admission or closed with a reason. A future admission date stays a draft until its date arrives. After admission, use Student Records for profile/lifecycle corrections rather than rewriting the admission draft.

Matching existing pupil names/admission numbers, active applications and draft names are surfaced for review. Existing admission numbers cannot be reused. If two children genuinely share a name, staff must document the distinction. Repeated submission of the same draft or approval does not create another pupil/account or reset a password.

CSV import accepts up to 100 pupils / 1 MB and validates all rows transactionally. Re-uploading the same row positions/details reuses draft keys. Different files may still contain the same child, so staff must review possible matches before admission. No name-matching import silently merges children or grants access.

Private document uploads accept PDF/JPG/PNG up to 3 MB each. Every uploaded file must be verified or superseded by a newer checked replacement before admission. Files remain private to authorized school staff; rejected copies and review history remain available.

## Manual versus automatic

Staff verify identity, guardianship, admission decisions, supporting documents and real payments. They choose class/session, whether access is needed and who may receive credentials.

The system handles transactional record creation, admission numbers, approved record links, initial-credential generation/expiry, password-change gating, connection counts and the activity trail. Class placement connects the pupil to class-based services, but teacher allocation, published reports, finance invoices and optional service assignments still depend on those modules' existing configuration.

## What was consolidated

The alternate Student Records creation form now points to the same school-led registration desk. Generic parent/student account creation and raw numeric family linking direct staff to the pupil-led verified setup. Existing Student Records, guardian records, application histories and family links remain intact.

## Source implementation

- `experience_admin.php`: `ar_*` registration/access schema, actions, guarded review, private document handlers, school-led screens; existing `ad_*` application route retained.
- `experience.php`: school-ID authentication alongside email, existing forced-password-change gate.
- `experience_ui.php`: clear sign-in/access-request labels, role welcome and pending approval guidance.
- `index.php`: additive activation, guided-route destinations and secure generic school staff issuance.
- `portal_collaboration.php`: school-scoped admission-family contact for explicitly linked pupils.
- `portal_experience.css/js/php`: responsive glass presentation, safe searchable selectors and refreshed asset versions.
- `affiliate.php`: dashboard/public-page pagination boundary.
- `experience_demo.php`: known additive registration tables in isolated-demo preparation/refresh; unexpected schemas still refused.
