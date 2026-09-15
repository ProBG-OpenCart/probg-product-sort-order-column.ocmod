# ProBG Product Sort Order Column

OCMOD modification for OpenCart 3 that extends the admin product list with **Sort Order**, **Product ID** and **Date Added** columns and allows both **Sort Order** and **Quantity** to be edited directly from the list.

## Support development

If this module is useful to you, you can support its development through Revolut:

[![Buy me a coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-Revolut-0075EB?style=for-the-badge&logo=revolut&logoColor=white)](https://revolut.me/vtotev)

## Features

- displays the `product.product_id` value in a dedicated **Product ID** column;
- displays the `product.date_added` value in a dedicated **Date Added** column;
- supports ascending and descending sorting by Product ID;
- supports ascending and descending sorting by Date Added;
- displays the `product.sort_order` value for every product;
- edits Sort Order directly in **Catalog → Products** without opening the product form;
- edits the product Quantity directly in **Catalog → Products**;
- saves Sort Order and Quantity changes asynchronously through AJAX without reloading the page;
- shows visual saving, success and error states for both inline editors;
- checks the standard `modify` permission for `catalog/product` before saving;
- validates submitted Sort Order and Quantity values as signed integers;
- updates the product `date_modified` value when Sort Order or Quantity changes;
- supports the standard ascending and descending sorting by Quantity;
- supports ascending and descending sorting by Sort Order;
- does not create or alter database tables;
- does not modify core files directly;
- uses OpenCart's standard product fields.

## Compatibility

Designed for OpenCart 3.x and checked against the standard structure of:

- OpenCart 3.0.2.0;
- OpenCart 3.0.3.7;
- OpenCart 3.0.3.9.

The modification uses stable controller, model and Twig locations shared by these OpenCart 3 versions. Starting with 1.3.1, the Product ID header and row cell are anchored to the Image column instead of the product-name cell, improving compatibility with other OCMODs that customize the product title cell.

## Installation package

The latest ready-to-install release package is version **1.3.1** and is available in:

`dist/probg-product-sort-order-column-1.3.1.ocmod.zip`

The archive contains `install.xml` in its root and can be uploaded directly through the OpenCart Extension Installer.

SHA-256:

`67e5a7d078d73af0ccbd9eb781b7baf486c3d0dc20313ce008a75c9a7bb15009`

Checksums for the available packages are also stored in `dist/SHA256SUMS`.

## Installation

1. Open the OpenCart administration panel.
2. Go to **Extensions → Installer**.
3. Upload the `.ocmod.zip` package.
4. Go to **Extensions → Modifications**.
5. Click **Refresh**.
6. Clear the Theme/SASS cache from Dashboard → Developer Settings if necessary.
7. Open **Catalog → Products**.

The product list contains sortable **Product ID**, **Sort Order** and **Date Added** columns. The existing **Quantity** column and the **Sort Order** column contain numeric fields that are saved automatically when changed.

## Inline editing

The Quantity and Sort Order cells use the same inline editing workflow. When a value changes:

1. the field is temporarily disabled while the request is being saved;
2. the module sends the product ID and the changed value to the admin controller through AJAX;
3. OpenCart checks the current administrator's `catalog/product` modify permission;
4. the value is validated as a signed integer;
5. only the selected field (`quantity` or `sort_order`) and `date_modified` are updated for the product;
6. a green check mark confirms a successful save;
7. on an error, the previous value is restored;
8. pressing Enter commits the current field through blur/change and does not submit the surrounding product-list form.

## Changelog

### 1.3.1

- fix: anchor the Product ID header directly after the Image header;
- fix: anchor the Product ID row cell directly after the product Image cell;
- fix: prevent column misalignment when another OCMOD replaces or extends the product-name cell in `product_list.twig`;
- chore: bumped the OCMOD version to `1.3.1`.
- chore: added the ready-to-install OpenCart 1.3.1 `.ocmod.zip` package under `dist/` and updated `SHA256SUMS`.

### 1.3.0

- feat: added a Product ID column to the admin product list;
- feat: added a Date Added column using `product.date_added`;
- feat: added ascending/descending sorting by `p.product_id`;
- feat: added ascending/descending sorting by `p.date_added`;
- feat: added English and Bulgarian labels for the new columns;
- fix: updated the no-results row colspan for the three additional columns.
- chore: added the ready-to-install OpenCart 1.3.0 `.ocmod.zip` package under `dist/` and updated `SHA256SUMS`.

### 1.2.0

- feat: added inline editing of product Quantity in the admin product list;
- feat: added AJAX Quantity saving without page reload;
- feat: added modify-permission, product existence and signed integer validation for Quantity changes;
- feat: update `date_modified` when Quantity changes;
- refactor: shared the client-side inline editor logic between Sort Order and Quantity;
- fix: corrected the documented SHA-256 checksum for the rebuilt 1.1.0 installation package;
- chore: added the ready-to-install OpenCart 1.2.0 `.ocmod.zip` package under `dist/` and updated `SHA256SUMS`.

### 1.1.0

- feat: added inline editing of product Sort Order in the admin product list;
- feat: added AJAX saving without page reload;
- feat: added modify-permission and signed integer validation before saving;
- feat: added visual saving/success/error feedback;
- feat: update `date_modified` when Sort Order changes;
- fix: prevent the Enter key in the inline editor from submitting the surrounding product-list form;
- fix: restore the previous value when an inline save fails;
- chore: added the ready-to-install OpenCart `.ocmod.zip` installation package under `dist/`.

### 1.0.0

- feat: added Sort Order column to the admin product list;
- feat: added ascending/descending sorting by `sort_order`;
- fix: updated the no-results row colspan for the additional column.
