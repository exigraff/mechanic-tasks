# Maintain inventory for a product bundle

* [task.json](../../tasks/maintain-inventory-for-a-product-bundle.json) (for import/export)
* [Task script](./script.liquid)

Use this task to automatically sync inventory for a simple product bundle – no theme modifications required. When configured with unique SKUs for the bundle and its components, and with quantities needed from each component for each bundle unit, this task keeps the bundle inventory set to the greatest possible value, given the quantities of its components. It also appropriately subtracts from component inventory whenever the bundle is ordered, and appropriately raises component inventory when a bundle order is refunded.

## Default options

```json
{
  "bundle_product_sku__required": "BUNDLE",
  "component_product_skus_and_quantities_per_bundle__keyval_number_required": {
    "BUNDLE-A": 1,
    "BUNDLE-B": 2,
    "BUNDLE-C": 3
  },
  "inventory_buffer_quantity__number": 1
}
```

## Subscriptions

```liquid
shopify/orders/create
shopify/refunds/create
shopify/inventory_levels/update
mechanic/user/trigger
```

## Documentation

Use this task to automatically sync inventory for a simple product bundle – no theme modifications required. When configured with unique SKUs for the bundle and its components, and with quantities needed from each component for each bundle unit, this task keeps the bundle inventory set to the greatest possible value, given the quantities of its components. It also appropriately subtracts from component inventory whenever the bundle is ordered, and appropriately raises component inventory when a bundle order is refunded.

Usage:

* Run this task manually to sync the bundle's inventory with that of the component product that has the least inventory in stock.
* This task will run automatically whenever the bundle product is ordered, and whenever the bundle product is refunded in such a way that it is restocked.

Requirements:

* This task does not support multiple inventory locations.
* Configure this task with unique SKUs for the bundle product and its component products. These SKUs must not be re-used for any other product variants in your store. However, any component SKU may be used for multiple copies of this task.
* Use the right-hand side of the "Component product SKUs and quantities per bundle" option to control how many units of each component SKU is required for each single bundle unit. If your bundle requires one wrench and two sprockets, for example, make sure to add "1" and "2" on the right-hand side, each number associated with the right SKU.

Notes:

* Whenever this task runs, manual inventory updates to the bundle product will be overwritten.
* Feel free to manually adjust inventory for component products. The bundle product's inventory will be synced appropriately.
* Use the "Inventory buffer quantity" option to artificially keep the bundle product's inventory lower than the actual available quantity.
