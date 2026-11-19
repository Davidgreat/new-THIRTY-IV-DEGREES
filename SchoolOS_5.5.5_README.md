# SchoolOS 5.5.5 — Familiar school report cards and receipts

## Install and find it
1. Keep a current backup.
2. Sign in with the real Platform Super Admin account and open Updates & Plugins.
3. Upload **SchoolOS_5.5.5_School_Document_Designs_Update.zip**, tick the trusted-source box and choose Verify & Install Update.
4. Sign in as a School Admin. Open **School settings → Document designs**. You can also follow the Report card & receipt designs link in the school-start step or the branding settings.

The update uses the existing school settings storage. It contains 44 approved application files, with a release manifest and verified hashes; no configuration, private keys, test database, source samples or SQL migration is included. Existing school records and previously configured academic formats remain in place. The tested updater supports rollback.

## One optional upload, one preview, one approval
Choose Report cards or Payment receipts. Select a clear PDF, PNG, JPG, WebP or Word .docx sample up to 8 MB. SchoolOS automatically suggests colours, logo placement, header treatment, table style and page orientation, using built-in fonts. Then choose **Use this design**. No manual field matching is required. Small adjustments are optional, under one closed section.

If you do not have an existing document, choose **Start with SchoolOS design**. Your saved school identity, logo and colours are used. Report and receipt styles are separate, so approving one does not overwrite the other.

## What the sample does—and does not do
PDF and image analysis use the first page. Word adaptation reads document/header styles, embedded logo candidates, page orientation and table structure. This is a style adaptation, not an exact document reproduction or an OCR/data-import tool. Fonts, subject fields and document content remain controlled by SchoolOS. Scans, unusual layouts, unrecognisable logos or complex documents may produce a simpler default layout. A clear image/PDF or the SchoolOS design remains available as a fallback. Legacy .doc files should be exported as PDF or .docx.

Your source file stays in the browser. The server receives only validated design choices and an optional small PNG logo suggestion. Names, marks, payment amounts and signatures in the source are not imported. Check a suggested logo in the preview; the saved school logo is preferred when available. The shared demo keeps its fictional school logo rather than saving uploaded logo suggestions.

Preview records are fictional and explicitly marked **SAMPLE PREVIEW — NOT AN ISSUED DOCUMENT**. The preview uses your school identity and, where present, an approved school report format and grading weights. Opening a preview does not create a student, publish a result, record a payment or activate a design.

## Connected to existing records
Approved appearance applies automatically to newly issued report cards and confirmed school-fee receipts through the existing print/PDF and parent-access routes. Approved academic formats, assessment weights, grade bands, complete published results, comments, attendance, school promotion decisions and verified parent-child relationships retain their existing controls. A design approval never changes scores, academic decisions or payment status. Receipt amounts and references continue to come from confirmed finance records.

Documents first issued after this update keep a shared immutable design/branding snapshot for reprints. A small reference is saved for each document, rather than duplicating a logo for every receipt. Newly approved styles apply to newly issued documents; the original styling of documents printed before this feature cannot be reconstructed automatically.

## Access and printing
Only a current, active School Admin can prepare or approve school designs. Drafts and snapshots are scoped to that school. CSRF validation and stale-preview checks protect approval. Parents, students and staff use the resulting documents only through their existing permissions; they do not receive editor access.

The editor fits mobile and desktop layouts and both themes. The standard tested report and receipt fit on one A4 page; longer reports paginate with repeated table headings, keeping all subjects and signatures. Print / Save PDF remains the normal document action.

## Bundled readers
PDF.js 5.4.394 and fflate 0.8.2 are bundled and served from this installation only, loaded when needed. No external conversion service or AI-provider account is required. License notices are included in the application helper and the accompanying third-party notices file.

## Validation
See the validation summary for local synthetic-data checks covering PNG/PDF/Word adaptation, invalid samples, school isolation, active-role and CSRF restrictions, stale approvals, preserved records, immutable/deduplicated styles, parent printing, responsive layouts, pagination, update installation and rollback. No production school records or external payments/messages were changed during testing.
