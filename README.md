# ProBG Product Sort Order Column

OCMOD modification for OpenCart 3 that adds a **Sort Order** column to the admin product list.

## Features

- displays the `product.sort_order` value for every product;
- supports ascending and descending sorting by Sort Order;
- does not create or alter database tables;
- does not modify core files directly;
- uses OpenCart's standard `sort_order` product field.

## Compatibility

Designed for OpenCart 3.x and checked against the standard structure of:

- OpenCart 3.0.2.0;
- OpenCart 3.0.3.9.

## Installation

1. Open the OpenCart administration panel.
2. Go to **Extensions → Installer**.
3. Upload `probg-product-sort-order-column.ocmod.zip`.
4. Go to **Extensions → Modifications**.
5. Click **Refresh**.
6. Clear the Theme/SASS cache from Dashboard → Developer Settings if necessary.
7. Open **Catalog → Products**.

A new **Sort Order** column will be displayed before Status.

## Changelog

### 1.0.0

- feat: added Sort Order column to the admin product list;
- feat: added ascending/descending sorting by `sort_order`;
- fix: updated the no-results row colspan for the additional column.
