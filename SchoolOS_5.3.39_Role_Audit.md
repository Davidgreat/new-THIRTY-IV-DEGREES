# SchoolOS 5.3.39 — Role-by-role audit

The profiles below are optional permission templates connected to shared school modules. They are not 29 mandatory posts or 29 separate applications. Every profile was created against a synthetic school, signed in, and routed to its working tools. All 35 public demo choices were also signed into the isolated sandbox.

Teacher and Admissions retain their existing dedicated portals and charts. The 27 Staff-type profiles now have job-specific overview cards, actual-record pies/charts and work links. Roles with multiple explicit grants can switch among their assigned overview desks. Counts never substitute sample values for an empty real school.

| Job profile | Working entry point | Requirements and boundary |
|---|---|---|
| Teacher | `?s=learning` | Current-session class/subject allocations; published/approved results and configured media service where used. |
| Admissions officer | `?s=applications` | School classes and registration policy; school-admin approval or explicit delegation for account issuance. |
| General school staff | `?s=tasks` | A linked active employment record for clock-in; only own tasks and permitted contacts. |
| HR & payroll officer | `?s=operations&area=hr&view=records` | Verified staff links; school payroll policy and independent review for protected actions. |
| School bus driver | `?s=operations&area=transport&view=today` | Verified driver profile, current licence, active route/vehicle and assigned pupils; collector checks remain required. |
| Transport coordinator | `?s=operations&area=transport&view=routes` | Verified drivers/vehicles, route schedules, stops and pupil assignments; capacity checks apply. |
| Boarding warden | `?s=operations&area=boarding` | Explicit hostel assignment; only assigned boarders; reviewed leave/physical handover requirements apply. |
| Boarding coordinator | `?s=operations&area=boarding` | Rooms, beds, warden accounts and pupil allocations; capacity and movement controls apply. |
| Librarian | `?s=services&area=library` | Catalogue/copies and actual borrowing records; no invented loans or ebook licences. |
| School store officer | `?s=services&area=inventory` | Stock/products/prices and real order states; invoices/payment and stock-reservation rules apply. |
| Communications officer | `?s=services&area=engagement` | Reviewed audiences, in-platform delivery and responses; external channels require consent and provider configuration. |
| Website editor | `?s=services&area=website&view=content` | School website record; identifiable content requires consent; publication needs another reviewer. |
| Website reviewer | `?s=services&area=website&view=approval` | Submitted content from another author; publication is independently reviewed. |
| School assets officer | `?s=services&area=inventory&view=assets` | Asset register/accounting details; care records and depreciation use actual recorded values. |
| Purchase reviewer | `?s=services&area=inventory&view=requests` | Pending requests/submitted orders from another author; purchasing and receiving remain with authorized store staff. |
| School reports viewer | `?s=intelligence&area=reports` | Permitted school aggregates and account-owned definitions/exports; no implicit finance or HR access. |
| Finance reports viewer | `?s=intelligence&area=reports&view=reports&dataset=finance` | Finance dataset only, plus its private exports/estimates; no fee-collection or bank-transfer power. |
| HR reports viewer | `?s=intelligence&area=reports&view=reports&dataset=hr` | HR aggregate dataset only and its private exports; no HR editing or implicit finance access. |
| Pupil support reviewer | `?s=intelligence&area=innovations&view=success` | Recorded evidence; insufficient observations do not create alerts. Human review never automatically sanctions a pupil. |
| Pupil collection officer | `?s=intelligence&area=innovations&view=pickup` | Current approved collector, linked guardian, one-time credential and physical identity check. |
| School workflow reviewer | `?s=intelligence&area=innovations&view=whatsapp` | A draft school message flow from another author. Approval does not itself send a message. |
| Curriculum coordinator | `?s=intelligence&area=academics&view=curricula` | School subjects, approved curricula/report formats and school calendar; independent approval remains required. |
| Timetable coordinator | `?s=intelligence&area=academics&view=timetable` | Verified teaching allocations, rooms, slots and availability. A proposal is reviewed independently and applied by the administrator. |
| Prepaid account cashier | `?s=intelligence&area=wallet` | School activation, guardian spending policy and verified funds. A different administrator verifies bank declarations. |
| Alumni officer | `?s=intelligence&area=governance&view=alumni` | Consented adult records and independent verification; pupil mentoring is supervised, not private adult-child messaging. |
| School review coordinator | `?s=intelligence&area=governance&view=accreditation` | School evidence, responsible employee and valid review dates. Recordkeeping does not certify legal compliance. |
| School group reports viewer | `?s=intelligence&area=governance&view=hq` | Explicit analyst grant and each school’s approved aggregate-sharing consent; no inherited pupil-record access. |
| School integration officer | `?s=intelligence&area=governance&view=plugins` | Approved bounded scopes and another reviewer; tokens expire and recheck current data permissions. Finance/HR require separate grants. |
| School privacy officer | `?s=intelligence&area=governance&view=privacy` | Documented school data purposes and verified requester authority; responses are reviewed, not automatic erasure or legal decisions. |

## Material defects corrected

- Finance Reports and HR Reports needed a general reporting capability that their presets did not grant. Each now works in its own dataset without broadening it to unrelated datasets.
- Shared-module defaults sent privacy, timetable, collection and integration staff to unrelated tabs. Defaults and menus now follow the actual role.
- A newly granted driver without a driver record could reach a false-to-null type error instead of a useful setup state. Missing driver records now produce the intended assignment prompt.
- Regular-collector handover incorrectly required the one-day collector type and could end the regular approval. Current regular approval now remains available for future days, with one-time/today handover safeguards.
- Fresh demos could mix database collations across base and later module tables. Academic-session, role/link and relevant contact comparisons now normalize their comparison without rewriting live school tables.
- Missing optional finance tables now produce a preparation state instead of querying an absent table.
- Manual reference/JSON fields and irrelevant website content fields made several valid workflows unnecessarily difficult to use. Named selectors, selections and conditional fields now reach the same validated handlers.

Existing integration staff are not automatically given wider live-school reporting access. Where an older account has only integration management, the overview explains the missing scope. An administrator reviews/reapplies that profile or adds the required reporting grant explicitly.

School-specific configuration and real external services still require school-side verification. The audit validates local code paths and scoped workflows; it does not certify every possible feature/state in a hosted production school.
