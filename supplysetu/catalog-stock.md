# Catalog, stock & locations

## Catalog

Admins define **what** can be stocked (item types, categories, custom fields). Store staff then add stock against those items.

1. Open **Administration → Catalog** → **Add item**.
2. Enter the name, minimum quantity (reorder level), and category (Asset, Supplies, Medicines, General, Others, or a blood bank type such as Bags, Kit, or Testing supplies).
3. Save, then use the **Parameters**, **Workflows**, and **Vendors** tabs for the item’s extra settings.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/supply-catalog-add.png" alt="Add catalog item" />
  <figcaption><strong>Add catalog item</strong>: name, minimum quantity, and category. Tabs along the top hold parameters, workflows, vendors, and movement history.</figcaption>
</figure>

## Stock

1. Open **Stock** / Inventory.
2. Filter by location, item, or low stock.
3. **Add stock** or receive from a purchase order put-away.
4. Transfer between locations when moving goods.
5. Print barcode labels from the item when needed.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/supply-stock.png" alt="Stock list" />
  <figcaption>Stock, with category tabs and the <strong>Set up your store</strong> steps: Locations → Vendors → Catalog → Stock. Stock stays empty until a catalog item exists.</figcaption>
</figure>

## Locations

Keep locations honest (Main store, OT, Blood bank fridge, etc.). Wrong location = wrong physical search during an emergency.

<div class="callout callout--tip">
  After PO goods arrive, finish <strong>stock intake / put-away</strong> the same day so dashboards match the shelf.
</div>

## Request inventory & stock requests

Departments ask the store for consumables instead of taking stock directly.

1. Open **Operations → Request inventory**. Stock is listed earliest-expiry first (FEFO); assets are not listed.
2. Add the items and quantities you need to the request.
3. The store approves or rejects it under **Stock requests**.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/supply-request.png" alt="Request inventory" />
  <figcaption>Request inventory: consumable stock by item, location, batch, and expiry — earliest expiry first.</figcaption>
</figure>

## Inventory movement

**Inventory movement** is the full audit trail of stock added, issued, adjusted, and transferred — with who did it and when. Use it to answer “where did this stock go?” before you adjust a count.

<figure class="media-frame media-frame--image">
  <img src="assets/screenshots/supply-movement.png" alt="Inventory movement" />
  <figcaption>Inventory movement: every stock change with item / batch, quantity, user, and notes.</figcaption>
</figure>
