# School OS 5.3.20 validation

Environment: local PHP/MySQL and Chromium. Dedicated fictional school/family fixtures were cleaned after testing. Production records were not accessed or changed.

## Server workflow and access — 19 checks passed

- Multi-child overview and direct child chat links.
- Mutual parent/child chat permissions; unrelated accounts refused.
- Published weighted results, grade bands and printable card link.
- School logo/name/motto/address/colour, learner identity, CA/exam marks and approved block order in report HTML.
- Other-family/tenant/term/format print attempts refused.
- Entirely missing or unapproved subject blocks complete report printing.
- Mismatched assessment/design weights refused.
- Child-scoped fee totals exclude void invoices.
- Attendance charts use recorded present/late/absent days only.
- All twenty parent features render without PHP warnings and retain the selected child.
- Assigned teacher, current timetable and child-specific library loan visibility.
- Released online homework and child-specific submission/feedback; unreleased activities hidden.
- Missing report format produces a setup explanation with published marks still visible.
- School class-format assignment preserves curriculum/calendar; parent assignment denied.
- School-only report notes, teacher/head comments, bounded term attendance and resumption date; parent edits/invalid dates refused.
- Guessed staff-only document/consent IDs rejected; published family documents accessible only for permitted child and active post.
- Cancelled checkout refused before provider invocation.
- Landing page rechecks account activation, including stale login snapshots.
- Revoked child link removes chat and report access.

## Browser — six end-to-end checks passed

1. Parent login opens family overview with both child chat shortcuts and two charts.
2. Parent sends a message to each of two children; separate student browser sessions receive and reply. Parent receives both replies.
3. Published results open the authenticated branded card; Chromium creates a printable A4 PDF.
4. All twenty parent views fit a 360px phone viewport without document-level horizontal overflow. Light/dark previews inspected; dark-mode light-panel contrast corrected. Wide tables scroll within their container.
5. School administrator assigns the existing approved report format through the actual form.
6. School administrator saves real report comments/term dates through the form; parent results and printable card display them. Updated PDF generated.

The preview logo was a synthetic test image; real logo loading depends on the school's configured image URL/file.

## Role regression

650 authenticated page visits across 14 existing demo account roles. No detected PHP warnings, fatal/parse errors or undefined function/method errors. This is a page-render regression check, not proof of all external service behavior.

## Package and updater — five checks passed

- Existing 5.3.19 updater restores every file after injected mid-deployment failure.
- Full install matches all 28 manifest file hashes; configuration hash remains unchanged and transaction journal commits.
- Reinstalling the same version is refused.
- Explicit rollback restores prior files and 5.3.19 metadata.
- ZIP traversal entries rejected before changes.

Package includes application files and release manifest only. No database dumps, configuration secrets, synthetic records or test scripts. Report notes use existing school setup storage; rollback retains that database data without exposing it through the older report renderer.

## Limits

Tests did not use the live authenticated school session, settle real Paystack payments or certify hosting/device behavior. School staff must configure branding, approve/assign the format, complete/moderate marks and publish each term. Missing comments/term dates are identified; no marks, signatures, historical enrolments or absence records are invented. Final hosted verification follows installation.
