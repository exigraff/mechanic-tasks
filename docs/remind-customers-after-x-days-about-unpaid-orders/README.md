# Remind customers after x days about unpaid orders

* [task.json](../../tasks/remind-customers-after-x-days-about-unpaid-orders.json) (for import/export)
* [Task script](./script.liquid)

This task wait for a configurable number of days (or hours!) after an order placed, and – if the order is still unpaid – emails the customer, and optionally adds a tag to the order. This task only sends one email – it does not send repeating reminders.

## Default options

```json
{
  "email_subject__required": "Don't forget! Order #{{ order.order_number }} still needs to be paid",
  "email_body__multiline_required": "Hi there,\n\nYour payment is still required! Please get in touch at {{ shop.customer_email }} to proceed.\n\nThanks,\n{{ shop.name }}",
  "tag_to_add_to_the_order": null,
  "number_of_days_to_wait__number_required": 7,
  "use_hours_instead_of_days__boolean": false
}
```

## Subscriptions

```liquid
shopify/orders/create+{{ options.number_of_days_to_wait__number_required | default: 7 }}.{% if options.use_hours_instead_of_days__boolean %}hours{% else %}days{% endif %}
```

## Documentation

This task wait for a configurable number of days (or hours!) after an order placed, and – if the order is still unpaid – emails the customer, and optionally adds a tag to the order. This task only sends one email – it does not send repeating reminders.
