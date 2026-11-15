# School OS 5.3.19 validation

Tests used local PHP/MySQL and isolated synthetic school records, cleaned after execution. No production records were changed.

## Workflow and access: 14 checks passed

- Regular collector registration stays pending until school approval.
- Unrelated-parent requests, driver approval attempts, invalid dates and invalid CSRF are refused.
- Regular approvals work across valid dates and stop outside their date range.
- Parent, school desk, driver dashboard and detailed trip views render approved collectors without PHP warnings.
- School-required one-time credentials and physical identity checks remain enforced.
- Parents can issue short-lived credentials against valid recurring approvals.
- Pending one-day replacements suppress regular collectors and block their existing credentials.
- Approved replacements take priority; cancelling restores regular approvals.
- Handover saves collector reference/name and the pupil's record and notification, consumes the credential and retains the recurring approval.
- Revocation blocks stale approvals and preserves earlier journey history.
- Inactive parent accounts or removed child links invalidate approval.
- School revocation works; an unrelated parent cannot revoke another family's approval.
- Day-specific approval is consumed after collection; the next day returns to regular collectors.
- Unrelated pupil and tenant records do not expose approvals.

## Browser: four checks passed

Chromium with separate parent, school administrator and driver sessions. Actual forms register and approve the regular collector, then board and hand over the pupil from the driver dashboard. The recurring approval remains approved after handover. The parent page fits a 390-pixel viewport without horizontal overflow.

## Regression and packaging

- 645 successful authenticated page visits across 14 existing demo roles; no detected PHP fatal/warning/undefined-function notices.
- ZIP contains 27 cumulative application files and a hash manifest; no configuration, credentials, database dumps, test fixtures or audit scripts.
- Collector availability for the driver roster uses bulk queries, rather than separate queries for each pupil.

## Existing updater: five checks passed

1. Injected mid-update failure restores every file.
2. Complete installation matches manifest hashes and writes the committed journal; config remains unchanged.
3. Duplicate version installation is refused.
4. Explicit rollback restores prior files and 5.3.18 metadata.
5. ZIP traversal entries are rejected.

These results validate the local implementation and package. The live deployment, browser permissions and your school's real account/route setup were not exercised here. No daily approvals were automatically converted into standing approvals.
