# School OS 5.3.8 — school book icons

Replaces decorative sparkle/starburst marks in the built-in interface with a plain open-book symbol and removes the decorative sparkle beside the account greeting.

Coverage includes the public website header/footer and promotional decoration, login/registration presentation, dashboard/sidebar branding, walkthrough buttons, admissions guidance, school setup/SmartStart links, Learning Studio badge and classroom waiting prompt. The public website's school-owner, guided-setup and parent-mobile preview images were recaptured from the updated application using fictional accounts, so those images no longer show the old icon either.

The replacement is a small inline SVG drawn with the current text colour; it needs no external icon service or font. Public image/script and Experience stylesheet cache URLs are refreshed. Existing customer-supplied school logo uploads are preserved.

This cumulative update retains the mobile waiting-room fix, automatic admission, account-aware wording, classroom interaction/media controls and earlier repairs. Account permissions, saved central LiveKit settings, student records and database schema are unchanged.

## Install

1. Back up files, database and private encryption keys; end active classes and test on staging.
2. Upload **SchoolOS_5.3.8_School_Book_Icons_Update.zip** through **Platform Super Admin → Updates & Plugins → Core updates**.
3. Confirm **5.3.8** and refresh dashboard, login and website pages. Close and reopen old browser tabs if they retain a previously loaded page.
4. Check the greeting, sidebar, login presentation and live-class waiting prompt. On the public homepage, check all three dashboard preview choices.

Existing live and demo accounts receive the updated interface without recreation. No media configuration needs to be re-entered.

## Validation

- Source scan found no remaining targeted sparkle/starburst glyphs or their encoded forms in active text assets.
- Browser checks passed for login, school-owner/teacher/student/parent dashboards, teacher classroom, phone waiting room and public homepage. Book icons rendered at the expected sizes, without browser/PHP errors.
- All three refreshed website preview images loaded successfully; screenshots use fictional records.
- Phone waiting layout still fits at normal zoom.
- All 589 role-page checks passed. Changed PHP/JavaScript syntax, package file hashes, installation, injected-failure recovery, same-version refusal, explicit rollback and traversal rejection passed.

Rollback: end classes, restore the updater's recorded 5.3.7 backup and refresh pages. The previous icon design and preview images will return; this release introduces no schema changes.
