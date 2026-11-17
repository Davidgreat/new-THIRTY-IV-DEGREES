# SchoolOS 5.4.0 — Modular roles and connected staff workflows

Cumulative update for the existing SchoolOS updater, including 5.3.40 and earlier changes. No configuration file, database credentials, private encryption keys or test records are included.

## Install and start

1. Keep a database backup and install `SchoolOS_5.4.0_Modular_Roles_and_Connected_Workflows_Update.zip` through the real Platform Super Admin updater. Upload the ZIP without extracting it. The current updater can install this package in one step.
2. Sign in as a School Admin and open **Roles & permissions**. If prompted, choose **Prepare roles & permissions**. On an existing school, services remain enabled initially to preserve availability. Choose the services the school actually uses; a small-school starting selection is provided.
3. Add only the role templates you need, review their permissions, then use **People & access** to assign one or several responsibilities to an existing employee. Use **Staff & access** to create a new employee login and HR connection first. Search employees by name or email instead of scrolling through the whole directory.

Creating a template does not create an account. The production school is never populated with all demo roles. Family identities, staff job responsibilities, partner accounts and platform administration remain separate.

## Existing accounts and deliberate migration

Existing employee accounts retain legacy access until reviewed. Assigning their first modular role explicitly switches their operational permissions to the reviewed assignments; add every responsibility they still need. Personal employment access and verified teaching assignments remain separate. Individual permission blocks override all role grants. Revocation and template changes take effect on later checks without requiring a fresh login.

Adding a new specialist profile through Staff & access connects its HR record and working role. When this upgrades an existing employee with legacy responsibilities, those existing capabilities are preserved in a labelled migration template for review. Previously unrestricted legacy financial approval is preserved in that template, rather than silently expanding or withdrawing it. Review and reduce that inherited ceiling deliberately.

New financial responsibilities start with an approval ceiling of **₦0**. Set a suitable ceiling before expecting that person to approve a payment. The recorder cannot independently approve their own payment, expense or refund. Manual confirmation records verified funds; it never initiates a bank transfer.

## School services and permissions

- Activate only the optional services the school uses. Switching a service off retains records and stops delegated access. School administrators retain setup and recovery authority.
- Build custom templates from the listed meaningful actions: viewing, adding, updating, archiving permitted completed records, approving, exporting, configuring and auditing, as applicable to the workflow.
- Assign multiple roles to one account. Scopes and financial ceilings apply separately to each assignment; an individual block overrides every grant.
- School Owner / School Admin privileges, subscriptions and platform administration are not employee permissions and cannot be delegated by a custom staff template.
- Keep read-only reports separate from transaction processing. View permission alone does not grant export or payment approval.

## Scope boundaries

Class and branch scopes are enforced in the new leadership, examination, accounts, counselling, pupil-related security, review and family-contact workspaces. Department scope is supported for staff review planning and assigned staff reviews. A branch here is within the same school tenant; separate school tenants continue to use the existing approved school-group sharing process.

Existing operational workspaces such as Library, HR management, Store and legacy aggregate Reports remain school-wide. They require school-wide grants; the assignment screen rejects unsupported narrower scopes instead of pretending to protect a screen whose underlying records lack that scope. Split responsibilities into separate roles when their valid scopes differ. A custom role never bypasses verified teacher/class assignments, parent/child links, driver/route assignments, independent approvals or cross-school isolation.

## New and extended working desks

- **Principal / Head Teacher:** scoped class and pupil counts, daily attendance overview, assigned teachers, published-result status and linked academic follow-up.
- **Examination Officer:** examination scheduling with class overlap checks; assessment setup in the existing academic records; independent mark moderation; validated publication into the existing family report-card flow.
- **Bursar / School Accountant:** shared-ledger pupil invoices, pending receipts, independent reconciliation, expenses and refunds; record scopes, approval ceilings, actual CSV export, scoped activity history and charts. School-prepaid and surplus-credit corrections require their appropriate reconciliation rather than an unsafe cash refund.
- **Guidance Counsellor:** encrypted support appointments and notes, appointment overlap checks, follow-up history and explicit export control. Academic leadership does not acquire counselling access merely by being a Principal.
- **Security Officer:** visitor arrivals and departures, pupil-linked or general incidents, follow-up, completed-record archive and activity history. This is a school record system; it does not operate physical gate hardware.
- **Review Coordinator / School Reviewer:** scoped review plans, independent assignment, reviewer findings and coordinator closure. Only the assigned reviewer receives reviewer access to a plan.

Existing specialist roles remain connected to their existing operational modules. Review coordination additionally connects to the new review-planning workflow. Family liaison permission allows verified parents and assigned staff to communicate within the permitted pupil scope; it does not open unrestricted staff-to-student chat. Upcoming class examinations appear to linked families.

## Practical controls

Counselling payloads are encrypted with the existing private application key. Back up that key alongside the database; installing this ZIP does not replace it. Important access changes and new workflow actions retain school-local history. Completed operational records are archived, not silently deleted from audit history. Financial records are corrected through controlled accounting workflows.

Record lists and audit history are paginated. Pupil lookup searches return at most 20 permitted matches. Workflow totals state their bounded record range; CSV and legacy report limits remain explicit. These are stored school records, not fabricated activity or bank balances.

## Demos and validation

There are 35 staff profile choices and 41 total demo identities, including family and ecosystem identities. Existing isolated demos upgrade additively; a demo-table inventory update preserves compatibility with the sandbox refresh safety checks. The 5.3.40 safe failure codes and private Demo health tools remain available.

See `SchoolOS_5.4.0_Validation.md` and `SchoolOS_5.4.0_Workflow_Matrix.md`. No hosted installation or live external payment/email was performed during testing.
