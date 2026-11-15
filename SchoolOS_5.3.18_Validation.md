# School OS 5.3.18 validation

Local validation on 15 November 2026 with fictional transport data.

## Populated transport views

- Passed: Active trip detail renders the real journey status helper
- Passed: Completed trip details render without undefined function errors
- Passed: Planned home trip details render their planned label
- Passed: History and selected-date report cards render completed and planned journeys
- Passed: All driver menu pages still render with populated trip data

## Authenticated browser

- Passed: Authenticated driver trip&trip=1 renders without the undefined-function error
- Passed: Authenticated driver trips renders without the undefined-function error
- Passed: Authenticated driver reports renders without the undefined-function error

## Installer

- Passed: Existing 5.3.17 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.18 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.17 metadata
- Passed: Traversal entries are refused before file changes

645 role-page visits across 14 synthetic roles passed without HTTP/PHP rendering failures or caught undefined-function/method/constant messages. PHP syntax passed. Populated view checks deliberately include active, completed and planned journeys so an empty history cannot hide the faulty helper call.

The package manifest hashes every shipped file. Configuration, credentials, local fixtures and database contents are excluded. The cumulative package retains 5.3.17 features, with the two escaping/helper call corrections and updated displayed release version. No database migration or business-data rewrite is performed.
