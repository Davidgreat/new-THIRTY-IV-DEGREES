# School OS 5.3.28 — Admissions desk

[Get the admin-installable ZIP on GitHub](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.28_Admissions_Desk_Update.zip)

Admissions welcomes prospective families, follows up enquiries, reviews pupil applications and documents, arranges assessments and visits, issues offers and hands accepted pupils into the school’s student records. The rebuilt desk keeps those tasks together with clear wording, glass panels, actionable totals, a stage doughnut and a 14-day application chart.

## Install

1. Back up school files and database.
2. Open the ZIP link and use GitHub’s **Download raw file** button.
3. Upload the ZIP in **Platform Admin → Core updates**, install and refresh the portal.
4. Sign in to the existing admissions account. Open **Admissions overview** or **Admissions desk**.

This cumulative package contains 34 application files and `release.json`. It keeps earlier updates and existing records; it adds no configuration, credentials, test data, new database tables or paid services. Installation and rollback were checked with the 5.3.27 updater. Existing admissions logins receive the new screens without being recreated. The school administrator must activate the existing admissions/CRM tables if not already active, and Student Records must be active before enrollment. Staff attendance continues to require HR’s verified employee-account link.

## The seven sections

- **Overview:** New applications, open offers, accepted files, unchecked documents, due reminders and unread family messages. Each total opens the corresponding work list. Charts have numeric breakdowns, including empty states.
- **Applications:** Search and paginated pupil cards. Each file has Review, Documents, Family conversation, Offer, Enrollment and Activity tabs. Pupil and guardian details are separate; actual school classes replace free-text class names. Office staff can correct pre-offer details with a reason. A changed guardian email revokes old private links and produces a replacement for identity-checked sharing.
- **Enquiries:** Capture a family’s contact and interest or follow a website enquiry. Conversion asks for the child’s own name, creates one application and retains the enquiry connection.
- **Reminders:** Follow-up dates, clear overdue/upcoming states and completion controls. Due reminders and new family application messages appear in the admissions account’s notifications.
- **Entrance tests:** Individual private invitations and a question bank controlled by the school administrator. A preparation page appears before the applicant presses Start. Each invitation retains its question set; the test allows one final submission within 45 minutes of starting.
- **Application form:** School-branded public application link, class selection, optional pupil background details and school questions. The administrator controls form opening and fee policy.
- **Reports:** Current-stage totals, enrollment share, application trend and how families found the school. These report recorded data rather than predicting admission quality.

On phones, navigation wraps into accessible buttons, forms stack, and the seven main sections and six file tabs were checked at 360px. Light and dark layouts retain readable text and chart labels.

## A family can participate before receiving a school login

Submitting a public application produces a private tracking link. Families can use it to see progress, review admission charges, upload supporting documents, exchange messages with admissions, see an interview time, open an entrance test and read/print a branded offer letter. They can accept or decline an unexpired offer there. Internal notes, interview comments and staff activity are kept out of this page.

Treat the private link as access to that application. The system stores its token hash; replacing the link revokes older copies. Share it only with the verified guardian. Documents are restricted to the school’s authorized admissions/admin accounts or that application’s private link, and are served as downloads. Allowed uploads are PDF/JPEG/PNG up to 3 MB. Existing old applications need an officer to issue their private family link.

School chat remains available for school colleagues and the relevant registered parent. Parents can contact the admissions office associated with their application or enrolled child. This does not grant unrestricted private chat with pupils or unrelated parents. The private application message page requires a refresh to show later replies; registered school chat retains its existing real-time behavior.

## Checked enrollment and finance boundaries

Enrollment requires an issued accepted offer, reviewed uploaded documents, administrator-confirmed admission charges, the offered school class and a staff review note. It creates the pupil, Student Records details, guardian relationship and admission event in one transaction. Approved parent/student logins can be linked during enrollment or afterward. Parent linking requires the recorded guardian email; student selection searches active, available school logins. Account approval and identity checks remain school responsibilities. No passwords or automatic account approvals are created.

Existing enrolled records are preserved; installing this update does not retrospectively create missing logins or rewrite pupil details. Older accepted applications without an offer require administrator review, a documented offer and renewed guardian acceptance.

Application and acceptance fees are snapshotted for new applications. The administrator checks actual payment externally, then records its reference; a reference cannot be reused for a different charge. **Finance → Admission payments** exposes the admission charge log. These confirmations do not automatically create student invoices, receipts, payment-gateway confirmations or accounting entries. Reconcile pre-enrollment money through the school’s approved Finance process.

The everyday desk no longer offers a queue-only email button or unrelated generic task creation. Family updates are explicitly posted in-platform; they are not presented as delivered email/SMS. Later changes to fees do not silently change existing applications.

[Audit findings](SchoolOS_5.3.28_Admissions_Audit.md) · [Validation](SchoolOS_5.3.28_Validation.md) · [Checksum](SchoolOS_5.3.28_SHA256SUMS.txt)

Validated locally with fictional school records. The update has not been installed or tested on the hosted school in this session.
