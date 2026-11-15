# School OS 5.3.19 — Regular collectors

[Download the admin-installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.19_Regular_Collectors_Update.zip)

Parents can register a regular school-bus collector for school approval once, covering a date range of up to one year. The driver selects that approved adult and verifies identity at each home drop-off. No new daily collector request is needed during the approved period.

## Install

1. Back up your files and database.
2. Download `SchoolOS_5.3.19_Regular_Collectors_Update.zip` using GitHub's Download raw file button.
3. Upload it in Platform Admin → Core updates and install.
4. Refresh the parent, school administrator and driver pages.

This cumulative package preserves existing accounts, route assignments, transport records and prior updates. It adds no database tables and requires no new service or paid integration. Existing day-specific approvals retain their original dates; they are not silently converted to regular approvals. The feature applies to existing real and demo accounts with the proper family and route links.

## Use

- **Parent:** Family Space → Safety & care → Collectors & pickup → Register a regular collector. Supply full name, phone, relationship/identity instructions and validity dates. Submit for approval.
- **School administrator:** Family Space → Collector approval desk. Verify the adult's identity and relationship and save an approval with a review note. Regular approval can be withdrawn immediately here.
- **Driver:** Driver dashboard → Today's pupils → select pupil → On home bus → Drop off. Choose the approved regular collector, check identity, enter a handover note and confirm. The detailed trip page supports the same collectors.
- **Different adult for one day:** Parent selects Someone different for one day. A pending change pauses regular-collector drop-off for that date. After school approval, only the approved one-day collectors are offered. Cancelling the one-day request restores eligible regular collectors; the following day returns to regular approvals automatically.
- **Remove regular collector:** The requesting parent can remove their collector approval; the school administrator can revoke it. Expired approval, inactive parent accounts and missing parent-child links are not accepted at handover. Stale driver forms are checked again when saving.

Regular approval remains reusable after a handover; each pupil's daily passenger record stores the approval reference, collector name, identity-check note and timestamp. Linked families receive the existing transport handover notification. One-day approvals are still consumed after collection.

If the school requires one-time pickup credentials, that setting remains enforced. Parents can issue a short-lived credential for an eligible regular collector in Collectors & pickup; it expires by midnight WAT and cannot be reused after handover. Regular collector authorisations are for the bus drop-off workflow; the separate campus pickup scanner retains its day-specific authorisation flow.

## Validation

Local validation passed 14 workflow/access checks, four browser checks covering parent registration, school approval and driver handover, 645 page visits across 14 roles, and five updater/rollback checks. See the versioned validation report. Installation on your live server is still required.
