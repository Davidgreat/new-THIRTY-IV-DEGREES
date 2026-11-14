# School OS 5.3.12 — school HR update

The Staff records screen previously combined directory creation, HR registration and login linking, with technical labels and unprefilled link controls. This release replaces it with a searchable staff register and a single Add staff member flow, plus prefilled View / edit screens.

## Staff register

- Full staff name and school job title identify the employee; department groups school responsibilities. The legacy free-text department field is removed from this workflow.
- Start date and monthly basic pay support employment and payroll. Basic pay may be left blank during induction; positive pay is required before activation.
- Teaching / non-teaching category and appointment type describe employment, independently of portal permissions and teaching allocations.
- Optional contact, emergency contact, qualifications and professional registration support school HR records. Emergency contact name and number must be provided together. These details remain within the employee's private HR record, available to that employee and authorised school HR users.
- Portal login is optional and selects an existing employee account. It gives access to the employee's own employment information; it does not create credentials or grant HR authority. Ask the school administrator to create a missing login. Existing links are prefilled; removing one requires confirmation. Student/parent and already-linked employee accounts cannot be assigned.
- One-step creation also creates four induction tasks: identity/contact, qualifications/references, appointment/policies and safeguarding/school induction. Complete these and confirm basic pay before activation. Existing active staff are not reset.
- Existing staff directory entries without an HR profile can be registered without duplicating the staff entry. Existing records can be searched by name, job or department. Staff references replace raw account/department IDs.

## Other HR sections

Sections are grouped into Staff & appointments, Attendance & duties, Pay & benefits, and Development & staff care. Each explains its purpose.

Recruitment progresses through shortlist, offer and hire; hiring creates an induction record without credentials. Appointment letters support open-ended permanent appointments or dated contracts. Duty assignments retain overlap checks. Appraisals remain private until published. Training and staff concerns have specific field labels. Exit clearance retains team checks, unsettled advance/payroll checks and explicit login-disabling confirmation.

Allowances and advances display naira amounts. Review controls select named records instead of requiring database numbers. Payroll records and released payslips identify staff/reviewers by name. Manual payment controls appear only to school administrators. Existing independent approval checks remain enforced on the server.

Payroll rules use ordinary percentages, naira relief amounts and editable annual band rows instead of basis points, kobo and JSON. Saved settings are prefilled. Each band width is an amount of annual income, not a cumulative ceiling; the last band covers remaining income. No statutory rates are invented or supplied automatically. A school must review its applicable rules.

## Installation

1. Back up the application and database. Test the update on a staging copy before using real payroll.
2. Install **SchoolOS_5.3.12_School_HR_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm version **5.3.12** and refresh open dashboard tabs.
4. Open HR → Staff register. Verify existing account and department links through View / edit. Fill missing appointment details when editing existing records; the update does not guess them.
5. Test one new staff member through induction and activation, then review payroll rules before preparing a future payroll month.

This cumulative package includes previous chat, classroom, notification and mobile fixes. Existing schools, demo accounts, staff links and historical payslips remain available. There is no schema migration or new provider setup. Extra private profile details use existing HR record storage; they are not published in chat/contact lists. The installer preserves config and records a rollback backup. Rolling back files retains entered HR data but hides the new profile interface; it does not reverse business actions performed after installation.

## Practical limits identified by the review

Attendance requires a linked staff login and uses self clock-in/out. There is no HR correction screen or biometric integration in this update. Leave is a request/review workflow, with overlapping pending/approved requests blocked; it does not calculate entitlements or balances. Payroll uses full monthly salary without automatic mid-month proration, absence deductions, overtime or year-to-date reconciliation. The tax model supports fixed annual relief and progressive bands; school-specific treatment must be reviewed. Payment confirmation records an external payment and accounting entries; it does not transfer money, file PAYE or remit pension. These are explicit limits, not completed features or a legal compliance certification.

See [HR audit and validation](SchoolOS_5.3.12_HR_Audit.md).
