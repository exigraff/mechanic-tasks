# Make products unavailable, after the date/time stored in product metafields

* [task.json](../../tasks/make-products-unavailable-after-the-date-time-stored-in-product-metafields.json) (for import/export)
* [Task script](./script.liquid)

Use this task to automatically set product inventory to 0, and the product's inventory policy to deny out-of-stock purchases, after a date/time that you specify in a product metafield.

## Default options

```json
{
  "datetime_product_metafield_namespace__required": null,
  "datetime_product_metafield_key__required": null,
  "datetime_format__required": "%Y/%m/%d",
  "run_hourly__boolean": null,
  "run_daily__boolean": null,
  "test_mode__boolean": null
}
```

## Subscriptions

```liquid
mechanic/user/trigger

{% if options.run_hourly__boolean %}
  mechanic/scheduler/hourly
{% elsif options.run_daily__boolean  %}
  mechanic/scheduler/daily
{% endif %}

mechanic/shopify/bulk_operation
```

## Documentation

Use this task to automatically set product inventory to 0, and the product's inventory policy to deny out-of-stock purchases, after a date/time that you specify in a product metafield.

Configure "Datetime product metafield namespace" and "Datetime product metafield key" with the namespace and key for the product metafield that holds a date/time value. Configure "Datetime format" with a valid date/time format, using http://www.strfti.me/ as a guide. This format must _exactly_ match the values you keep in your product metafields. If a value is found that does not match this format, this task will skip that product.

Configuring product metafields requires an app for metafield management. [Metafields Guru](https://apps.shopify.com/metafields-editor-2) is a good choice. :)

When you run this task (or as it runs hourly/daily, per your configuration), the task will look for products who have a date/time value that's in the past. For qualifying products, all inventory items with a level greater than 0 will have their levels set to exactly 0, and all variants will have their inventory policies set to "deny" (preventing sales, once the variants are all out of stock).
