# ProBG Product Sort Order Column

OCMOD modification for OpenCart 3 that adds a **Sort Order** column to the admin product list and allows the value to be edited directly from the list.

## Support development

If this module is useful to you, you can support its development through Revolut:

[![Buy me a coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-Revolut-0075EB?style=for-the-badge&logo=revolut&logoColor=white)](https://revolut.me/vtotev)

## Features

- displays the `product.sort_order` value for every product;
- edits Sort Order directly in **Catalog → Products** without opening the product form;
- saves changes asynchronously through AJAX without reloading the page;
- shows visual saving, success and error states;
- checks the standard `modify` permission for `catalog/product` before saving;
- validates that the submitted Sort Order is an integer;
- updates the product `date_modified` value when Sort Order changes;
- supports ascending and descending sorting by Sort Order;
- does not create or alter database tables;
- does not modify core files directly;
- uses OpenCart's standard `sort_order` product field.

## Compatibility

Designed for OpenCart 3.x and checked against the standard structure of:

- OpenCart 3.0.2.0;
- OpenCart 3.0.3.9.

The modification uses stable controller, model and Twig locations shared by these OpenCart 3 versions.

## Installation package

The ready-to-install package for version **1.1.0** is available in:

`dist/probg-product-sort-order-column-1.1.0.ocmod.zip`

The archive contains `install.xml` in its root and can be uploaded directly through the OpenCart Extension Installer.

SHA-256:

`abf4d5c4feaa5c0ea3a3d2b0557b6f987136697aff136100ff2d1bc2000be172`

## Installation

1. Open the OpenCart administration panel.
2. Go to **Extensions → Installer**.
3. Upload `dist/probg-product-sort-order-column-1.1.0.ocmod.zip`.
4. Go to **Extensions → Modifications**.
5. Click **Refresh**.
6. Clear the Theme/SASS cache from Dashboard → Developer Settings if necessary.
7. Open **Catalog → Products**.

A new **Sort Order** column is displayed before Status. Change the numeric value in the field and the module saves it automatically.

## Inline editing

Each Sort Order cell contains a number field. When its value changes:

1. the field is temporarily disabled while the request is being saved;
2. the module sends the product ID and new Sort Order to the admin controller through AJAX;
3. OpenCart checks the current administrator's `catalog/product` modify permission;
4. the value is validated as an integer;
5. only `sort_order` and `date_modified` are updated for the product;
6. a green check mark confirms a successful save;
7. on an error, the previous value is restored.

## Changelog

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
