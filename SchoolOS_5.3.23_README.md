# School OS 5.3.23 — Empty-chart hotfix

[Download the installable hotfix](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.23_Empty_Charts_Hotfix_Update.zip)

Fixes `max(): Argument #1 ($value) must be of type array, int given` on the librarian overview/reports and its automatic chart refresh when both recent request and return datasets are empty. Older loan records can still exist while the recent chart has no data.

The previous expression reduced to `max(1)` in that case. PHP treats a single argument as the array form of max(), so the integer caused a TypeError. The chart now passes a nonempty array with a scale floor of one. Empty periods show zero bars and a clear message: “No requests or returns recorded in the last 14 days.” No activity is invented.

The same vulnerable expression in the teacher timetable infographic is corrected for accounts with no assigned periods.

## Install

1. Back up the platform files and database.
2. Download `SchoolOS_5.3.23_Empty_Charts_Hotfix_Update.zip` using GitHub's Download raw file button.
3. Upload and install through Platform Admin → Core updates.
4. Refresh the librarian dashboard.

The cumulative update preserves existing accounts, books, copies, loans, reservations, charges and previous features. It adds no tables and requires no data reset or reactivation. The library footer identifies version 5.3.23.

Local validation reproduced the exact error using the old code, then checked empty/older-only/request-only/return-only/mixed datasets, complete overview/report pages and the empty teacher timetable. Browser and refresh API checks passed, along with 651 authenticated page visits across 14 roles and five installer/rollback checks. See the validation report. Installation on the live site is still required.
