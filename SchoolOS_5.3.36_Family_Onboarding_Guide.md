# Family onboarding guide

## Parents

Use the unique link supplied by the school. Enter your name, relationship, email and WhatsApp number, then add each child separately. Supply their name, date of birth, class/arm, gender and admission number if known. Student access is optional; parents may assist younger pupils. A form supports up to ten children.

Confirm your authority and submit. Nothing is automatically admitted or granted access. Keep the private return link for progress, requested corrections or another sibling. Approved entries and verified parent identity cannot be rewritten through the public form. Contact the school if the return link is lost.

After school approval, access instructions include the login URL and parent/approved student sign-in IDs. New accounts have single-use setup links valid for 72 hours. Choose a personal password, then sign in. Existing personal passwords remain unchanged. Keep setup links private; never send a password back to the school.

## School office

For manual entry, open Admissions → Family onboarding → Add a family manually. This uses the same reviewed process as a parent-submitted form.

For each child:
1. Cross-check details against school records. Search by name/admission number and compare supporting details; suggestions do not prove identity.
2. Select an existing pupil where available, preserving their school records.
3. Create a missing record only after verification. Confirm class/session and original admission date, and explain possible duplicate matches where applicable.
4. Select an existing parent account/guardian contact when they exist. Accounts in another role or school are not repurposed.
5. Verify guardian authority and control of both email and WhatsApp contacts, record a verification note and decide whether student access is needed.
6. Save a verified match for approval, or approve immediately if authorized.

School administrators approve by default. Explicit school-admin delegation may allow admissions to approve reviewed family/student accounts; it grants no administrator roles. Approve all reviewed children handles saved verified matches together. Other children may remain pending or need correction. An invalid batch rolls back its new approvals/accounts rather than leaving a partial batch.

Repeated form keys/approvals/delivery retries do not create another pupil/account or reset a personal password. The same pupil cannot be approved twice within a family form. Corrected child/contact details invalidate older prepared matches.

## Corrections and identity reuse

Return a child with a clear correction note. The parent reads it through their private return link and resubmits the unapproved details. Verified staff may replace a lost return link, revoking the older copy.

One parent account covers siblings on the verified family request. Existing school parent accounts must be explicitly selected where available. An inactive pending account can be verified/approved; deliberately disabled accounts require a separate administrator review.

Staff who are also parents may receive a separate parent school-ID account using their verified contact email without changing their staff account. Existing student accounts keep their passwords and remain linked to exactly one pupil.

## Delivery

| State | Meaning |
|---|---|
| Email queued | Awaiting the immediate attempt or queued-mail worker |
| Sending email | A worker has claimed this handover |
| Email sent · SMTP accepted | SMTP server accepted it; inbox delivery is not confirmed |
| Delivery failed | Check selected sender configuration and contact information before retry |
| Delivery uncertain | Check the inbox before manually repeating an interrupted send |
| Replaced by a newer handover | A newer message supersedes an unsent older version |

Approval commits before sending. Email problems do not undo school enrollment. Retrying preserves personal passwords and refreshes eligible initial setup links where needed. Queued messages refresh current setup instructions before dispatch.

Open WhatsApp handover opens the supplied number and prepared instructions. Staff review and send the message themselves. The audit records opening, not confirmed sending/delivery. Only an authorized account approver handles private setup instructions.

School administrators may choose shared platform SMTP or their own verified school service. School credentials are encrypted and school-scoped. A failing selected school service does not silently fall back to a different sender. Test the real hosting service with an inbox you control; sender/domain authentication and actual mailbox delivery remain operational checks.

The workflow connects verified identities and school records. It does not import historical results, attendance or balances, create payments/invoices, or assign optional bus/boarding services.
