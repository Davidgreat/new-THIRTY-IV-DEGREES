# SchoolOS 5.3.39 — Working staff profiles and branded family registration

[Open the installable ZIP on GitHub](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.39_Staff_Workspaces_and_Branded_Family_Update.zip)

This review found that the 29 job choices in 5.3.38 were permission presets, not 29 separately developed applications. Several specialist profiles landed on an unrelated first tab; Finance Reports and HR Reports were blocked by a general reporting prerequisite. This update connects the profiles to relevant overviews and working, permission-filtered school tools.

## Staff dashboards

- All 29 job profiles have working entry points. Teacher and Admissions retain their established role portals. The 27 profiles using the underlying Staff account type now have role-specific overview panels, current record counts, status pies, date/workflow charts and direct work links.
- Counts come from actual, school-scoped records. Driver and warden counts are constrained to assigned work; private exports and API keys are constrained to the account. Empty schools show empty states, not invented activity.
- Existing driver, HR, boarding, library, store and communications daily controls remain connected. Relevant menus lead into shared operational modules rather than 29 duplicate codebases.
- Specialist module tabs now follow their permissions. Timetable staff land on timetable tools, privacy staff on privacy tools, collection staff on collection tools, and integration staff on integrations. Unrelated or unusable tabs are filtered.
- Finance-only and HR-only reporting accounts can use their own reports and private exports without general school-report access. Each still lacks the other's private dataset.
- Integration officer presets now include standard school aggregate reporting, needed by their read-only API workflow. Finance and HR remain separate permissions. Existing live account grants are not silently expanded: an older integration account without reporting access shows a setup prompt, and the school administrator can review and reapply its profile in Staff & access.
- Named selectors replace manual reference numbers in key review, asset, procurement, website, timetable, privacy, report-export and collection forms. Long lists can be searched locally.
- Timetable periods, curriculum subjects, report columns and integration scopes use selections instead of requiring users to write JSON or reference lists. Core validation and independent approval remain enforced.
- Website content fields follow the chosen content type. A news writer does not have to fill tour, staff-profile or gallery fields.
- Verified collection works for approved regular collectors without cancelling future authorization. A used credential cannot authorize another handover that day. Expired credentials are displayed as expired in the overview.
- Prepaid cashiers can request funding and record permitted purchases. Bank verification remains an independent school-administrator action, and the interface now reflects that boundary.

These are optional job templates. A school does not need to employ 29 people or enable every module. See the [role-by-role audit and prerequisites](SchoolOS_5.3.39_Role_Audit.md).

## Complete demo coverage

The login page now offers **35 searchable demo choices**: the 29 staff profiles plus School owner, Parent/guardian, Student, Partner, Platform overview and School reviewer.

The existing marked, isolated demo upgrades on its next login. It adds missing role accounts, employment links and fictional example workflows; it keeps existing accounts and passwords. Fresh demo provisioning also includes all profiles. It never copies live school users, data or provider credentials.

Examples connect an editor to an independent reviewer, staff purchasing to a purchase reviewer, school evidence to review, pupil-support alerts to recorded attendance, and timetable proposals to real allocations. The sandbox prepaid example uses fictional declarations and credits only. A bank declaration still needs verification by a different demo administrator before a cashier can spend it.

The original Teacher and Communications demos retain their previously seeded additional capabilities. Real schools choose explicit job profiles and additional grants for their own employees. Demo access requires the platform's isolated database configuration; displaying a selector does not replace that setup.

## Parent registration and school branding

The form now shows the actual school name, configured logo or school initials, motto and school contact details. Its accent buttons follow the school's primary colour with automatically selected readable text. If an incomplete branding record has a blank name, the real school name is used instead.

Parents follow three steps: parent details → children → check and send. They can add siblings, move back without losing entries, and review the details before submission. Phone screens use a compact introduction and expandable school contact details. Light/dark themes are supported.

The existing verification workflow remains in place: public submission creates a pending family request. It does not admit pupils, issue accounts or grant access to school records. The school's existing family review, identity checks and approval are still required. The fictional preview is labelled and refuses submissions.

Configure school branding under School admin → School settings → Advanced → School Branding (`?s=school_setup&view=advanced&module=branding`). The form uses the same branding source as other school documents.

## Cleaner shared family links

New shared links omit the visible `index.php`:

- Demo preview: `https://getschoolos.com.ng/?family=preview`
- School family link: `https://getschoolos.com.ng/?family=YOUR_SCHOOL_TOKEN`

Use the generated school link from Family onboarding; do not replace its token manually. Existing `index.php?family_join=...` and `index.php?family_demo_preview=1` links continue to work. Private progress/setup links also use the installation root when generated.

`index.php` is the PHP entry point, and query parameters are valid routing. This portable improvement requires no Apache/Nginx rewrite changes and supports installations in a subfolder. Completely path-based URLs such as `/family/join/...` would require compatible hosting rewrite rules. Private dashboard routes are not being advertised as path-only URLs in this release.

## Install

1. Back up application files and the database.
2. Download the ZIP above using GitHub's Download raw file button.
3. Install through Platform Super Admin → Core updates, then refresh open tabs.
4. Open school-admin Staff & access to review profiles. New employee logins retain the connected HR/dashboard setup from 5.3.38.
5. Sign out and reopen login to see the complete demo picker. A configured isolated demo upgrades automatically on first connection; a destructive refresh is not required for this update.
6. Open Family onboarding and copy the newly displayed school link. Check the school branding and submit a fictional test family before sharing widely.

The update contains 41 approved files plus release.json. Configuration, credentials, private keys, fixtures and test scripts are excluded. It introduces no new production tables. Normal school records and existing account grants are retained; existing workspaces must already be prepared where their features are used.

Some functions deliberately require setup or review: driver licences and route assignments, hostel assignments, current teaching allocations, school website preparation, school-group consent, prepaid activation/guardian policy, provider credentials and independent approvals. These are real controls, not simulated success buttons. File rollback does not undo later approvals, passwords or database changes.

[Validation](SchoolOS_5.3.39_Validation.md) · [Role audit](SchoolOS_5.3.39_Role_Audit.md) · [Checksum](SchoolOS_5.3.39_SHA256SUMS.txt)

Tested locally. This session did not install the update on the hosted school or validate its real external providers.
