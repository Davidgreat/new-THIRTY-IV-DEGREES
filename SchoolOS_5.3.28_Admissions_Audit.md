# Admissions audit — 5.3.28

Reviewed the 5.3.27 application source and exercised the updated portal locally on PHP 8.4/MariaDB with fictional school records, 16 November 2026. This is an implementation audit and local validation, not a certification of the hosted server or its operational practices.

## Findings and changes

| Finding in the preceding admissions implementation | Result in 5.3.28 |
|---|---|
| Generic ecosystem landing page, dense CRM navigation and technical labels made the admissions job hard to follow. | Dedicated role landing page; seven task-focused sections; contextual six-tab applicant file; plain wording, glass panels, actionable metrics, stage pie and daily application chart. |
| School-office creation exposed a class text field; enquiry conversion could copy an adult’s name as the pupil. | Separate guardian/pupil fields, actual tenant-scoped class selection, explicit conversion and one enquiry/application connection. |
| Missing correction workflow encouraged duplicate applications for typing errors. | Audited pre-offer correction form, active-identity duplicate checks, guardian-email change revokes previous tracking access. Offered/enrolled identity changes remain outside this quick correction flow. |
| A raw stage change could accept a file without documenting a valid offer. Review and assessment paths could move an accepted file backwards. | Accepted stage requires an issued unexpired offer and acceptance evidence. Dedicated offer/enrollment actions, checks on assessment/interview changes and a preserved activity trail. |
| Offer issuance did not require review of uploaded files; rejected document replacements had no clear completion path. | Pending/rejected uploads block offers and enrollment. Newer checked files can supersede earlier files of the same document type, retaining the old record and review notes. |
| Public application receipt and staff-only CRM did not provide a full family progress/response workflow. | A hashed-token private family page supports status, documents, messages, interview time, test invitation, offer letter and acceptance/decline. Link replacement revokes previous access; internal notes are excluded. |
| Email queue controls could appear to provide a working outbound conversation without demonstrating delivery. | New desk uses explicitly labeled in-platform family updates. Legacy queued-message records are retained and labeled; no new transport or worker is claimed. |
| Admission payment confirmation was unavailable in the everyday CRM, while unpaid charges could block enrollment. | School-admin-only external-payment confirmation, charge locking, duplicate reference guard and an admission payment log under Finance. No fabricated payment-provider success or automatic duplicate student invoice/accounting entry. |
| Enrollment inserted a pupil but did not complete guardian/account and Student Records handover. | Transactional pupil/profile/guardian/admission-event creation; optional verified approved parent/student account links; later link completion; conflict guards and offered-class enforcement. Student Records activation is required. |
| Copying/opening an entrance link could start its timer, later question edits could affect an invitation, and attempts could be reissued. | Explicit preparation and Start step, saved per-invitation question set, fixed server deadline, single final submission and no reset from repeated invitation creation. Closed admission stages stop old test links. |
| Existing role contacts did not support the full admission family conversation. | Same-school admissions/parent chat tied to a recorded guardian email or enrolled-child relationship. Ordinary student restrictions remain; unrelated families do not become available to the officer. |
| Follow-ups and family replies lacked a focused role-specific work queue. | Due reminder/unread family message metrics, filtered lists, completion/read actions and admissions notification integration. |
| Browser icon fallback could render a workspace and consume a one-time success message between POST and redirect. | Icon probes return 204 before sessions/workspace rendering. Admission success feedback also participates in the existing save-tone mechanism. |

## Access and data connections

Every admissions mutation checks CSRF and a fresh active school admin/admissions identity. Application, class, document, charge, enquiry, reminder, metadata and enrollment lookups are school-scoped. Transactions and record locks protect the main multi-record workflows. Student account search returns at most 20 active available school logins. Invalid private links and unrelated staff-document requests are refused.

A private applicant link intentionally grants access to that applicant’s family page and documents. Tokens are generated randomly and only hashes persist in application metadata. The pages use no-referrer and no-store responses. A fresh link is shown once to staff for sharing; it must not be forwarded to unrelated people. This is not an email-ownership verification service.

Admissions handles prospective-family care and the pupil handover. School administrators retain fees, payment confirmation, public form settings, question-bank changes and portal-account approval. Admissions staff can link existing approved accounts after their explicit identity review; they cannot approve an unverified account through the new desk. Existing HR attendance access and school community/chat remain available.

The public website enquiry table feeds the desk. The public application creates a CRM application and its fee snapshot. Enrollment connects the existing Students, Student Records, guardian relationships and approved account-link tables. Parent and student dashboards were opened after enrollment to check the resulting connection.

## Existing data and operating limits

- The package uses existing tables and does not purge prior applications, documents, events or enrolled pupils. Existing admissions logins use the new UI. It does not invent missing historical profile data or retroactively link logins by a similar name.
- Legacy accepted files without an offer cannot silently pass the new checks. The administrator can document the missing offer and require renewed acceptance. Existing enrolled files can use the reviewed account-link completion form.
- The school defines which supporting documents and admission criteria are required. The update verifies the review status of uploaded files; it does not supply a mandatory national admission-document policy.
- Fee snapshot guarantees apply to applications created through this update. Older records retain their saved charges and use the existing policy when a missing acceptance charge is first created.
- Pre-enrollment charges remain a separate confirmation log. The school must reconcile money into its approved accounting process and issue official financial documents through the relevant Finance workflow.
- Entrance tests provide a bounded single-submission assessment, not remote invigilation. An expired attempt cannot submit a late final answer; there is no automatic draft saving or late grading. Offline interruptions need school follow-up.
- The dashboard refreshes summary counts every 30 seconds when visible and idle. Applicant/family pages do not provide a live push conversation; later replies appear on refresh. Due reminders appear when the admissions portal polls its notifications.
- Hosting upload limits must permit a 3 MB file; private file storage and database backup capacity remain hosting responsibilities. No real email/SMS/payment service or production device was exercised during this audit.

See [validation](SchoolOS_5.3.28_Validation.md) for the exact local checks and [installation notes](SchoolOS_5.3.28_README.md) for deployment.
