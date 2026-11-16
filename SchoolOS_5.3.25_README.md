# School OS 5.3.25 — Store product photos

[Download the admin-installable ZIP](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.25_Store_Product_Photos_Update.zip)

Storekeepers can add an optional product photo when creating or editing an item. Existing items can receive photos without changing stock, prices or order history. Normal edits preserve the photo; uploading a replacement changes it, and Remove current photo clears it.

Parents see searchable product cards with the image, item/size name, price, quantity and a request button tied to that item and their selected child. Students see the same product imagery in the existing school-store catalogue. Tapping a photo opens a larger view inside the page; Close photo or Escape returns to the shop. Items without a photo have a clear placeholder. Images and cards fit small phone screens.

## Install and use

1. Back up application files and database.
2. Open the ZIP on GitHub and choose Download raw file.
3. Install through Platform Admin → Core updates, then refresh.
4. In the store account, open Items & stock → Add item or Edit item.
5. Choose a JPG, PNG or WebP product photo, wait for Photo ready, and save the item. Offer the item in the family shop with a positive price and available stock for parents to request it.

No paid image service or new database table is needed. Photos are stored with existing school-scoped setup records and are included in database backups. The cumulative ZIP includes the earlier store and portal updates. It contains 32 application files plus release.json, with no configuration, credentials or test records. Existing items begin with a placeholder until their school adds photos.

## Image handling

The browser prepares photos up to 8 MB and 24 megapixels, scales them to a maximum edge of 1,280 pixels and compresses them to at most 350 KB before upload. Server validation independently checks the actual image bytes, dimensions and type. Where PHP GD is available, the server also resizes/re-encodes accepted raster images. Without GD, already prepared images remain supported; oversized originals are rejected with guidance. SVG, executable files and corrupt images are refused. Public upload folders and original filenames are not used.

Image requests require an active school account and the same school as the item. Families and students can retrieve only photos of listed store items; stock managers can view their school's internal/unlisted item photos too. Images are served with an explicit raster content type, nosniff and private/no-store headers. Photos are not available anonymously.

Ordering, stock reservation, invoices, payment confirmation, collection and return records continue to use the existing workflows. A product photo is current catalogue information, not an immutable historical receipt image.

## Validation

Seven real-browser photo checks cover multipart upload/compression/preview, preserved edits, parent/student catalogue and phone layout, enlargement and parent request, replacement, forged SVG rejection, account/school/listing access and removal. Four additional image-validation groups and the 19 store workflow regression checks passed. Five installer/rollback checks passed. These are local tests with fictional records; this update has not been installed on the hosted school in this session.
