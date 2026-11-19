# SchoolOS 5.5.8 — One consistent platform workspace

## Install
Keep a current backup, sign in with the real Platform Super Admin account, open Updates & Plugins, upload **SchoolOS_5.5.8_Unified_Platform_Workspace_Update.zip**, tick the trusted-source box and choose Verify & Install Update. Refresh the dashboard after installation.

## What changes
Overview and the main platform management pages now share the same platform sidebar, official SchoolOS logo, header, theme control and circle-animation engine as Platform settings, Plans & billing tools, Updates & plugins and Integrations. You no longer switch between the platform sidebar and the older school-style sidebar for these pages.

The three tool entries remain grouped below daily work: Platform settings, Plans & billing tools, and Updates & integrations. The last entry provides two clear tabs: Updates & plugins and Integrations. The current entry stays visible in the horizontal menu on phones.

Settings put registration and the installation address first. Occasional service controls sit in four closed sections: Live classroom connection; Demo sandbox & maintenance; Account recovery; Workspace health & diagnostics. All existing forms and submitted field names are retained, including provider settings, sandbox maintenance, recovery, package controls and updater actions. Credentials issued through verified recovery remain visible as a copy-once notice. Feedback after saving remains visible.

The background uses the existing school-dashboard movement engine, with large restrained circles, colour cycling, elastic motion and the desktop animation fallback. It starts automatically; there is no play-background step. It pauses for hidden pages/printing and respects reduced-transparency and forced-colour settings. Existing mobile reduced-motion behaviour is unchanged. Hover and keyboard-focus feedback use the shared interaction implementation.

## What stays connected
Existing URLs, POST handlers, permissions, CSRF checks, service/callback endpoints, package prices, school records and billing rules remain in their existing workflows. This change does not grant school or delegated platform staff access to Super Admin tools. School dashboards and support-visit restrictions retain their own appropriate contexts. Public website pages and printable/service views remain separate contexts.

This cumulative update retains People & capacity, document designs, the ROI calculator and the official logo correction. It contains the approved application files and verified release manifest, with no configuration, credentials, uploads, test data or SQL migration.

## Validation
Local synthetic-data checks covered original form/field preservation across all four tool pages; settings saving and feedback; updater CSRF rejection; one sidebar and current menu; theme persistence; mobile/desktop layouts; actual circle movement under normal and reduced desktop animation settings; colour cycling; hover feedback; school-account isolation; clean subfolder routes; installer/rollback behaviour; and an actual upload through the old Updates form that installed 5.5.8 and returned to the new shared frame. No production school or payment records were changed.
