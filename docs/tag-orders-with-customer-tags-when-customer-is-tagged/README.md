# Auto-tag orders with customer tags when new customer tags are added

* [task.json](../../tasks/tag-orders-with-customer-tags-when-customer-is-tagged.json) (for import/export)
* [Task script](./script.liquid)

Activating this task will automatically keep the order tags up to date with the customer's tags.

## Subscriptions

```liquid
shopify/customers/update
```

## Documentation

Activating this task will automatically keep the order tags up to date with the customer's tags.

When a customer is updated, this task will go through each of that customer's past orders and add all of the customer's current tags as order tags (if any new tags are found).
