# School OS 5.3.26 — Product options and stock studio

[Download the admin-installable update](https://github.com/Davidgreat/new-THIRTY-IV-DEGREES/blob/main/SchoolOS_5.3.26_Store_Product_Options_Update.zip)

The school-store product form now adapts to the item group. A product can have multiple selected sizes/packs and colours, with a separate opening quantity for every combination. The page has a photo panel, three clear sections, touch-friendly choices and a live total. Parents and students see grouped products and select the exact available stock option before requesting it.

## Install

Back up application files and database. Download the ZIP with GitHub's Download raw file button and install through Platform Admin → Core updates. Refresh the page afterwards. The cumulative ZIP includes the previous portal/store/photo updates and preserves existing records. It contains 32 application files plus release.json, without configuration, credentials or test data. No new tables, paid service or manual bootstrap installation are required. The installer and rollback were tested against the existing 5.3.25 updater.

## Product groups

| Group | Available option fields |
|---|---|
| Uniform / clothing | Preset letter, numbered and age sizes; multiple colours |
| Sportswear | Clothing/team sizes; multiple colours |
| Footwear | EU shoe sizes; multiple colours; optional custom size labels |
| Book for sale | Book formats and optional edition/year; no colour controls |
| Stationery / school shop | Packs/boxes; optional colours for products such as pens/folders |
| Food & drinks | Portions/packs and optional flavour/type; no colour controls |
| School-use supplies | Units/packs/cartons; no colour controls |

Preset buttons and the full size selector avoid repeatedly typing common sizes. A custom size/pack label is available for a school's own sizing system. Category-specific drafts keep their options when switching groups; an edition does not become a food flavour.

## Create and maintain options

1. Open Items & stock → Add an item. Enter the product name, group, selling price and optional photo.
2. Choose sizes/packs using preset buttons or Add option. Selected chips can be removed.
3. Where relevant, select several colour swatches or use the colour picker and Add colour.
4. Enter the verified opening units against each size–colour combination. The total updates as you type.
5. Enter opening unit cost, optional code prefix/location/count note and the low-stock level per option. Enable Offer in the family shop when appropriate.
6. Save product & stock options. Every combination receives its own inventory ID, item code, movement record and availability. A supplied code prefix gets numbered suffixes. Invalid or duplicate combinations roll back the complete batch.

Up to 60 combinations can be saved together. Zero is allowed for an out-of-stock option; it is excluded from family requests until stock becomes available. All initial options share the entered selling price and cost. Individual option prices can subsequently be edited. Each later delivery, stock correction, order reservation, collection and return uses the existing stock/Finance workflow for its specific option.

To add further sizes/colours to a new-style product, open one of its options → Edit item → Add sizes / colours to this product. Existing stock remains unchanged. Choose only the new combinations and enter their verified opening counts. Use Restocking for later purchased deliveries.

Editing an existing option preserves its current quantity and carrying cost. Product identity stays consistent across its options. An option with order history cannot be repurposed as a different size, colour or edition. Use a separate new option for that change. The existing referenced correction controls remain available in Items & stock.

## Colours and photos

The picker derives a familiar colour family such as Red, Blue, Green, Black or White from the selected shade. Exact hexadecimal values and swatches are preserved. Several different reds can coexist; their exact codes distinguish the shades. Names are automatic colour-family descriptions rather than supplier-specific shade names.

The initial product photo is shared efficiently across its options. Edit a specific option to give it its own replacement photo if needed. Removing a shared source photo restores the placeholder for options still using it. Image compression, upload validation, protected delivery and enlarged in-page previews continue from 5.3.25.

## Parent/student shop connection

A new-style product appears as one card with a size/colour, format or pack selector. The selected option updates price, stock count, colour swatch, photo and maximum request quantity. The form submits that exact inventory ID. Approval rechecks availability and reserves only that option; its invoice, payment and collection continue through the existing child-specific Finance workflow. Other sizes and colours are unaffected.

Search returns up to 20 matching products and includes their available, listed options. Parents retain the selected-child restrictions and student accounts retain their existing child links. Stock/procurement permissions remain enforced on the server.

Existing standalone items retain their original labels and history. They remain visible and editable; this update does not guess how to merge historical items into a product family. Newly created products use the new builder and grouping.

[Validation results](SchoolOS_5.3.26_Validation.md) · [SHA256 checksum](SchoolOS_5.3.26_SHA256SUMS.txt)

Validated locally with fictional school records. This session did not install the ZIP on the hosted school or process real payments.
