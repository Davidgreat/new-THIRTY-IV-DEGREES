# SchoolOS 5.3.38 — School administration and connected staff onboarding

[Open the installable ZIP on GitHub](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.38_School_Admin_and_Staff_Onboarding_Update.zip)

The school administrator now has a connected command centre, a practical first-use setup guide and a clearer way to bring existing school staff onto SchoolOS. The Parents and Teachers placeholders have been replaced with real school-scoped directories.

## Install and start

1. Back up application files and the database.
2. Download the ZIP above using GitHub's Download raw file button. Install it through Platform Super Admin → Core updates.
3. Refresh open tabs. Open School admin → School overview, then Setup guide.
4. If preparation is required, expand Prepare or update installed workspaces. This prepares installed tables without deleting existing records.
5. Follow the setup guide: school identity, operational classes/subjects/session, pupils, staff access, teacher allocations, family links and privacy. Optional checks cover assessment configuration, calendar, finance and SMTP. Configure and test external services before relying on them.

The admin overview includes setup progress, active-account bars, pupil attendance and invoice-position charts, pending reviews and direct working links. Compact reminders appear across school-admin pages while essential records are missing. Checks report records/configuration found, not certification of accuracy or live service delivery. Past-session teacher allocations and assessments do not complete current-session checks.

## Add school staff directly

School admin → Staff & access → Add a staff member:

- Enter the person's name and optional email.
- Choose their real working dashboard: teacher, admissions, HR/payroll, driver, transport, boarding, librarian, school store, communications, website work and other supported specialist profiles. There are 29 named choices, mapped to existing permissions.
- Select an existing unlinked HR record if the employee is already recorded. Teachers can explicitly select an existing unlinked teacher directory record. Names and emails do not silently merge records.
- For a new HR record, enter the actual employment start date. Confirm active employment only when verified; otherwise HR induction must be completed before clock-in is enabled. Existing HR status, start date and salary are retained.
- Verify identity/employment/access, then create the connected login.
- Privately hand over the one-time school sign-in ID and temporary password shown immediately. It expires in 72 hours. The person must choose a personal password at first login.

Creation connects the login, staff directory, HR record, and chosen job permissions in one transaction. A teacher additionally receives a teacher-directory link. New salary information is left for HR; licence details, routes, hostel assignments and teaching allocations are not invented.

Open View access & next steps for an existing staff member to connect their records or add another dashboard of the same account type. Existing permissions are preserved; permissions are removed through the relevant Operations, Services or Intelligence access settings. Disabled accounts are not silently reactivated. School-administrator access cannot be self-granted through these profiles.

Finance reports viewer provides reporting access; fee collection and invoice administration remain school-administrator functions. Optional prepaid and school-group services still require their existing administrator setup and scope controls.

## Invite existing school staff

School admin → Setup guide → People & access, or Staff & access → Invite existing school staff:

1. Enable staff requests. Public school listing is optional.
2. Copy the private staff invitation and send it to your school staff. It includes this installation's Join a school URL and the school's unique code.
3. Staff submit their name, email, job request and a school reference. No password is needed at this stage.
4. Requests remain inactive. The school administrator checks identity and employment, chooses the approved dashboard, explicitly selects any existing HR/teacher records and approves or rejects the request.
5. Approval connects the records and permissions and shows one-time temporary sign-in details for private handover. The staff member sets a personal password at first sign-in.

The platform's member-registration setting must also permit requests. If disabled, the admin page explains the restriction; direct staff creation remains available. Invitation possession alone never grants account access.

Parents and pupils continue to use the separate Family onboarding flow and the existing multi-child parent link. Staff signup cannot grant parent/pupil access or infer family authority. Legacy family requests are directed to verified Family & login setup.

## Directories and maintenance

- Parents & guardians shows actual parent accounts and verified child links. A separate searchable guardian-contact directory shows family records, avoiding assumed matches between a contact and a login.
- Teachers shows directory records, linked logins and valid current-session allocations. Unlinked teacher accounts have clear connection actions.
- Staff & access has search, pagination, employment status, dashboard labels, staff chat and clear next steps.
- Account connections shows staff/teacher record links by name. An administrator can remove a verified incorrect directory link with an audit reason, retaining the login and HR record, then reconnect the correct record. HR links, class allocations and job permissions are reviewed separately.
- Searchable account recovery accepts names, email or school sign-in IDs. School IDs use the correct P/S/T/E/A prefix. Verified recovery shows its temporary credential once and replaces the old password.

Glass styling, personal welcomes, existing animated backgrounds and family-onboarding features remain included. Phone/desktop layouts support both themes. Existing accounts and records are read directly; installing does not grant every existing staff account new permissions. The school administrator reviews each person's actual job and links.

## Package and limits

Cumulative update: 36 approved files plus release.json, with no configuration, credentials, keys, test scripts or synthetic data. No new database tables are introduced by this release; required existing workspaces must be prepared where not already installed.

File rollback restores files/version metadata, not staff approvals, password changes or database records created after installation. Preserve database backups and plan account handover before rolling back.

Shared demo pages show existing fictional records; live staff invitation, permission changes and credential issuance remain disabled in the shared demo. Local tests used synthetic ordinary school accounts. This session did not deploy to the hosted school or test its real SMTP/payment/media providers.

[Validation](SchoolOS_5.3.38_Validation.md) · [Checksum](SchoolOS_5.3.38_SHA256SUMS.txt)
