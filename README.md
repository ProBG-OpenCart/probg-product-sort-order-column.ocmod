# ProBG Product Sort Order Column

OCMOD modification for OpenCart 3 that adds a **Sort Order** column to the admin product list and allows both **Sort Order** and **Quantity** to be edited directly from the list.

## Support development

If this module is useful to you, you can support its development through Revolut:

[![Buy me a coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-Revolut-0075EB?style=for-the-badge&logo=revolut&logoColor=white)](https://revolut.me/vtotev)

## Features

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
- uses OpenCart's standard `sort_order` and `quantity` product fields.

## Compatibility

Designed for OpenCart 3.x and checked against the standard structure of:

- OpenCart 3.0.2.0;
- OpenCart 3.0.3.9.

The Quantity cell markup used by the modification is identical in the standard product list templates of both checked versions. The modification uses stable controller, model and Twig locations shared by these OpenCart 3 versions.

## Installation package

The ready-to-install package for version **1.2.0** is available in:

`dist/probg-product-sort-order-column-1.2.0.ocmod.zip`

The archive contains `install.xml` in its root and can be uploaded directly through the OpenCart Extension Installer.

SHA-256:

`acfa83ff6991ac3d4b4d623bb33e6f6c2b47b0603e160ac4da560b552e95f5fa`

Checksums for the available packages are also stored in `dist/SHA256SUMS`.

## Installation

1. Open the OpenCart administration panel.
2. Go to **Extensions → Installer**.
3. Upload `dist/probg-product-sort-order-column-1.2.0.ocmod.zip`.
4. Go to **Extensions → Modifications**.
5. Click **Refresh**.
6. Clear the Theme/SASS cache from Dashboard → Developer Settings if necessary.
7. Open **Catalog → Products**.

A **Sort Order** column is displayed before Status. Both the existing **Quantity** column and the **Sort Order** column contain numeric fields. Change a value and the module saves it automatically.

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
- chore: added the ready-to-install OpenCart `.ocmod.zip` package under `dist/`.

### 1.0.0

- feat: added Sort Order column to the admin product list;
- feat: added ascending/descending sorting by `sort_order`;
- fix: updated the no-results row colspan for the additional column.
