# Auto-archive orders after fulfillment

* [task.json](../../tasks/auto-archive-orders-after-fulfillment.json) (for import/export)
* [Task script](./script.liquid)

Just as it says. :) Archives orders immediately upon fulfillment, or after a configurable number of days.

## Default options

```json
{
  "days_to_wait_after_fulfillment_before_archiving__number": null
}
```

## Subscriptions

```liquid
shopify/orders/fulfilled{% if options.days_to_wait_after_fulfillment_before_archiving__number %}+{{ options.days_to_wait_after_fulfillment_before_archiving__number }}.days{% endif %}
```

## Documentation

Just as it says. :) Archives orders immediately upon fulfillment, or after a configurable number of days.
