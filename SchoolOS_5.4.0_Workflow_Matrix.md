# SchoolOS 5.4.0 implementation map

| Area | Working connection | Access and control |
|---|---|---|
| School services | Tenant-local service selection, small-school starter selection, setup prompts | School Admin only; records retained on disable |
| Permission templates | Ready-made templates and custom action lists | Versioned changes, disable/re-enable, no portal-identity escalation |
| Employee responsibilities | Existing employee lookup, several assignments on one account, HR-linked new specialist accounts | Explicit adoption, immediate revocation, individual denies, per-assignment ceilings |
| Class / branch scope | Class directory, branch-to-class mapping, scoped new workspaces | Database scope filtering plus record checks; other tenants refused |
| Department scope | Existing HR departments and employee-linked review plans | Staff review records only; unsupported scope/workspace combinations rejected |
| Teacher duties | Existing teaching allocations plus optional additional roles | Teaching remains tied to verified class/subject assignments |
| Principal | Pupil attendance, class teachers, result publication status, academic actions | Assigned school/classes/branches; no automatic confidential counselling access |
| Exams | Class schedule conflicts, shared assessments, existing score moderation and term publication | Weight and completeness checks; own-score approval/publication refused |
| Accounts | Canonical invoices, payments, journal, expenses, refunds and family balances | Independent approvers, per-transaction ceilings, tenant and pupil scope |
| Report exports | Existing report definitions and CSV pipeline, new workflow CSV | Separate export permission; scheduled workers recheck permission |
| Counselling | Appointment and support record, follow-up history, conflict checks | Encrypted payloads, scoped access, explicit export |
| Security | Visitor arrival/departure and incident follow-up | School or pupil scope; completed records archived with history |
| Independent reviews | Coordinator plans, assignment/reassignment, reviewer findings, coordinator closure | Reviewer must have matching scope; no self-assignment or self-approval |
| Family conversations | Existing school chat, verified parent links, scoped staff liaison | Reciprocal contacts; no blanket non-teaching access to students |
| Family examination awareness | Upcoming scheduled class examinations | Linked children’s class only; no confidential case payloads |
| Existing operations | Transport, boarding, library, store, assets, HR, communications, website and governance remain connected | Existing record-level guards retained; legacy school-wide workspaces require school scope |
| School-group reports | Existing approved membership and sharing | Separate school consent; report access does not permit cross-tenant edits |
| Archive and audit | Access changes, workflow follow-up, completed-record archive, accounting activity | No deletion of financial ledger or audit history |
| Demo migration | Previous 35 identities plus six specialist staff profiles | Marked isolated database only; preserve password hashes and HR history |
| Existing updater | Cumulative 41-file package using approved destinations | Manifest hashes, rollback journal, configuration preserved |

Scope is intentionally constrained to the record models that support it. The UI and backend reject unsupported scopes instead of silently widening them. Family and platform identities are not employee job profiles.
