# School OS 5.3.27 — Communications desk

[Download the admin-installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.27_Communications_Desk_Update.zip)

The school communicator keeps families and staff informed: school notices, reminders, urgent updates, events, newsletters, polls and enquiries. The desk now centres on those responsibilities with a dedicated staff landing page, clear navigation, glass panels, delivery-outcome pie, 14-day activity chart and small-screen layouts.

## Install

1. Back up application files and database.
2. Download the ZIP using GitHub's Download raw file button.
3. Install through Platform Admin → Core updates and refresh.
4. Log in to the communications account. Its existing Communications manager assignment is required; the school administrator manages assignments in School Services access controls.

The cumulative update preserves existing records and earlier updates. It contains 34 application files plus release.json; no configuration, credentials, test records, new tables or paid services are added. Installation, injected-failure recovery and explicit rollback were tested against the existing 5.3.26 updater.

## The eight everyday sections

- **Overview:** Six actionable totals, delivery-outcome pie, daily activity chart, role guidance and links to drafts, inbox and messages needing attention.
- **Write a notice:** Relevant fields for each notice type, audience selection, bounded person/class name search, saved-message selection, send time and optional external channels. Save a draft, review it in Notices, then publish or schedule.
- **Notices:** Searchable draft/published/scheduled/stopped records. Edit a draft, publish, make a copy or stop remaining delivery. Draft revision checks prevent overwriting a colleague's changes. Repeated form submissions and publishing do not duplicate the notice or recipient records.
- **Events & polls:** Dates, poll choices, aggregate response bars, cancellation and closure. Cancelling a published event marks its calendar entry cancelled; closing a poll preserves its existing responses.
- **Family & staff inbox:** Your own recent conversations and name search for parents/colleagues. Open the existing real-time chat to talk, with its typing indicators and reactions. The desk does not expose conversations you are not a member of.
- **Contacts:** Find submitted email/phone details by name, confirm ownership with a staff reference, and see saved channel choices. A changed address must be checked again. Communications staff cannot grant another person's external-channel consent.
- **Saved messages:** Reusable notice titles and bodies. Use a saved message directly in compose; choose Write my own message to edit wording. Approved WhatsApp template details remain optional advanced fields.
- **Delivery reports:** Per-notice and per-recipient outcomes with clear labels, failure guidance, full notice text, explicit portal read confirmations and poll results. Provider acceptance is distinguished from confirmed delivery/read status.

Technical provider secrets, message allowance allocation and generic personal task creation are removed from the communicator's everyday navigation. Sending credentials and allowance changes stay with the school administrator. Staff attendance, school chat and separately assigned website-news duties remain accessible without mixing payroll, inventory or library management into this desk.

## Connections and account boundaries

Parents can find and chat with their school's active communications office. Communications staff can initiate/reply to parents and school colleagues. Ordinary staff do not acquire the same parent access; student private-chat permissions remain within existing family/assigned-teacher relationships. Communicators send student updates through scoped notices. School and active-account checks remain in place, and revoking the communications assignment removes that additional parent-chat access.

Published notices reach the selected audience in Community Hub and in-platform notifications. Ordinary broadcasts use a shared audience-scoped Hub post, retaining one delivery record per recipient. Personalised messages remain recipient-specific. Personal-post filtering happens before feed limits, preventing large recipient batches from hiding another person's alert.

Class events appear in the appropriate parent's selected-child calendar and the student's announcement area. Polls appear in the relevant Family Space feedback page and Community Hub/student update areas. Choices, publication state, audience and closing time are checked on the server; one account contributes one response. Explicit Mark as read actions feed the notice report. Availability in the portal is not automatically counted as someone reading it.

## Immediate and scheduled delivery

Publishing processes up to 100 due in-app delivery records. A visible, idle communications desk continues processing due in-app records every 30 seconds. Larger batches continue across those bounded runs. The existing school worker is required for reliable unattended delivery when the desk is closed; the page is not a replacement for a background scheduler.

The school administrator can use the existing cPanel/CLI worker, for example:

```text
php /absolute/path/public_html/services_worker.php --tenant=SCHOOL_ID --limit=100
```

Run it regularly using the hosting account's scheduler and actual PHP executable/path. In-app delivery uses no messaging credits. External delivery still requires the school's configured email/SMS/WhatsApp/push service, verified contacts, the account holder's or linked parent's applicable consent, internal message allowance and the worker. Existing provider charges may apply. The dashboard's refresh processor handles in-app delivery only. Configuration presence does not prove a provider connection.

Stopping a notice prevents remaining queued delivery; it cannot recall already sent messages. Unknown external outcomes are shown for checking rather than automatically retried. Urgent school notices still need the school's normal emergency contact procedure when immediate confirmation is essential.

[Audit findings](SchoolOS_5.3.27_Communications_Audit.md) · [Validation](SchoolOS_5.3.27_Validation.md) · [Checksum](SchoolOS_5.3.27_SHA256SUMS.txt)

Validated locally with fictional school records. This session did not install the update on the hosted school or send real external messages.
