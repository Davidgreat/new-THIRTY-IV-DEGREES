# School OS downloads

## Latest: 5.3.18 — trip display hotfix

[Download the installable hotfix](SchoolOS_5.3.18_Trip_Display_Hotfix_Update.zip?raw=true)

[Installation and fix details](SchoolOS_5.3.18_README.md) · [Validation report](SchoolOS_5.3.18_Validation.md)

Corrects the misspelled `etm_journey_label()` calls in trip details and trip cards. The proper calls escape the output of the existing `tm_journey_label()` helper. Existing transport, attendance and parent-chat records are retained; no configuration or database change is required.

Install through **Platform Super Admin → Updates & Plugins → Core updates**, confirm **5.3.18**, and refresh driver tabs. Back up first. This cumulative hotfix retains the home non-travel and staff-attendance changes from 5.3.17.

Validated: five populated transport-view scenarios, three authenticated driver browser pages, 645 role-page checks and five installer/recovery scenarios. The page scanner now detects handled undefined-function/method errors as well as HTTP/PHP warnings.

SHA-256: `c252465a16df3bfcb268ffadef6476b9816a68aa71a602213af0c727508ac445`

## Earlier releases

[5.3.17 home travel and staff attendance](SchoolOS_5.3.17_README.md) · [5.3.16 daily pupil records and parent chat](SchoolOS_5.3.16_README.md) · [5.3.15 driver workspace](SchoolOS_5.3.15_README.md) · [5.3.14 HR command centre](SchoolOS_5.3.14_README.md) · [5.3.13 staff profiles](SchoolOS_5.3.13_README.md) · [5.3.11 typing reliability](SchoolOS_5.3.11_README.md)
