# Communications audit — 5.3.27

Scope: available School OS source, local PHP/MySQL and Chromium. The user's authenticated hosted-school browser was not available in this session.

The communicator's responsibility is school information and conversation: notices, reminders, events, newsletters, parent/staff enquiries, contact quality and delivery follow-up. Admissions decisions, payroll, student records, stock management and provider-secret administration remain in their own assigned roles.

| Finding | Resulting change |
|---|---|
| Generic staff landing page with mixed task/service navigation | Dedicated communications overview and eight focused sections; separately assigned work stays accessible. |
| Provider credentials and internal credits beside everyday communication actions | Removed from the communicator's daily menu; credential and allowance changes remain administrator-only. |
| Campaign terminology, raw account IDs and comma-separated channel names | Notice-based wording, contextual fields, class/person name search, channel controls and per-record actions. |
| Parents could not reach communications staff in chat | Bidirectional same-school parent/communications contact permission, named office context and inbox links. Ordinary staff/student permissions remain scoped. |
| Drafts had no clear edit/review workflow | Edit, revision check, copy and contextual publish/schedule. Nonce/source keys prevent duplicated drafts; repeated publishing preserves recipient uniqueness. |
| Immediate in-app publication depended entirely on manually running the old queue | Publish-time bounded processing plus visible-desk refresh; existing background worker retained for unattended scheduling. |
| Per-recipient posts crowded large-school feeds before visibility checks | Shared posts for ordinary broadcasts; recipient filtering before personal-post limits. Personalised messages stay separate. |
| Events/polls existed apart from parent calendar and student update areas | Audience-scoped event/poll cards integrated with those account views and existing notifications/Hub. |
| Poll could be answered while scheduled but not actually published | Publication proof, audience/time/choice checks and helpful duplicate-vote handling. |
| Finished delivery made upcoming events/polls appear impossible to cancel/close | Contextual Cancel event/Close poll actions retain delivered records and responses. |
| No useful distinction between availability, provider acceptance and a person's read | Clear status labels and separate explicit portal read confirmations. |
| Contact verification used IDs and could race an address change | Named contact cards, ownership reference and locked address comparison. Consent remains separate. |
| Limited operational reporting and narrow-screen flow | Six linked totals, accessible delivery pie/legend, 14-day bars/text breakdown, poll response bars, paginated cards and 360px layouts. |

Access was checked through current school accounts, existing role grants and server-side scope validation. Search is bounded to 20 names; contacts and delivery lists are paginated. No cross-school recipients or campaign/template references are accepted. Revoked communications access stops future sending and the extra parent-chat relationship.

The audit does not certify live hosting, real school data, external provider credentials/delivery, emergency procedures or legal compliance. No records were deleted from the hosted school. Post-install checks should confirm the actual role assignment, scheduler, audience/class links, contact ownership/consent and school-approved wording.
