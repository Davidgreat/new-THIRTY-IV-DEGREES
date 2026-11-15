# School OS 5.3.18 — trip display hotfix

A typo introduced in 5.3.17 combined the HTML-escaping helper and the trip-label helper into the nonexistent call `etm_journey_label()`. It affected the trip-detail header and trip cards used by history/reports.

Both sites now correctly call `e(tm_journey_label(...))`. The real label helper already existed. This is a PHP display correction; it does not require a setting, provider or database change. Existing transport, staff attendance, pupil, parent-chat and other business records are retained.

## Install

Back up, install **SchoolOS_5.3.18_Trip_Display_Hotfix_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**, confirm **5.3.18**, and refresh the affected driver tabs. Open a trip, Trip history and Reports. The dashboard version badge also shows 5.3.18.

The package is cumulative and retains the 5.3.17 home-plan, drop-off guidance, staff clock-in/out and Admissions attendance fixes. See the [5.3.17 feature guide](SchoolOS_5.3.17_README.md) for those workflows; use 5.3.18 as the installed-version confirmation.

## Verification

Populated active, completed and planned trip details were tested, along with history/report cards and all six driver menu pages. Authenticated driver browser checks passed for trip details, history and reports. The role-page scanner now also detects caught “Call to undefined function/method” and “Undefined constant” messages rendered inside a page, rather than relying only on HTTP status or uncaught PHP warnings. Installer deployment, recovery and rollback checks passed.

No production session was accessed or updated by these local tests. [Validation results](SchoolOS_5.3.18_Validation.md).

File rollback returns to the prior files, including the prior display error. It does not undo saved business data.
