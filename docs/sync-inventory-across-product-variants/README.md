# Sync inventory across product variants

* [task.json](../../tasks/sync-inventory-across-product-variants.json) (for import/export)
* [Task script](./script.liquid)

Useful for multiple price points, or for offering customizations of the same item, this task lets you offer multiple variant listings for what is ultimately the same stock. A purchase of a particular variant results in the inventory for all other variants, for the same product, being lowered by the amount ordered.

## Default options

```json
{
  "product_types_to_monitor__array_required": [
    "Shirt"
  ]
}
```

## Subscriptions

```liquid
mechanic/user/trigger
mechanic/scheduler/10min
```

## Documentation

Useful for multiple price points, or for offering customizations of the same item, this task lets you offer multiple variant listings for what is ultimately the same stock. A purchase of a particular variant results in the inventory for all other variants, for the same product, being lowered by the amount ordered.

### Getting started

1. Populate the list of product types that you'd like this task to monitor.
2. In the Shopify admin, navigate to the Products > Inventory area. Use the tools here to ensure that all products, for the types you care about, have all their variant inventory in sync.
3. Back in Mechanic, click the "Run task" button. Mechanic will scan your products, and cache the current inventory level for each one.
4. Wait! :) Every ten minutes, Mechanic will check your inventory, and make any adjustments necessary to keep everything in sync. For example, if three different inventory items - within the same product - are each sold three different times, Mechanic will ensure that each of those items are lowered by a further 6, and that all others are lowered by 9.

### Notes

* This task only works with a single location. Multiple locations are not supported.
* To manually change inventory levels for a product, adjust _only one_ variant to the desired level. During the next scheduled run, the task will bring the other variants into sync.
* By default, Mechanic will check your inventory every 10 minutes. Feel free to change that subscription to "mechanic/scheduler/hourly", or [something else that suits your needs](https://help.usemechanic.com/events/all-event-topics#mechanic).
