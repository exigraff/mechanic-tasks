# Auto-tag customers within a purchase range

* [task.json](../../tasks/auto-tag-customers-within-a-purchase-range.json) (for import/export)
* [Task script](./script.liquid)

Use this task to auto-tag customers when their historical purchase total falls within a certain range. For example, by configuring this task to evaluate purchase thresholds by number of orders, and by setting the minimum to "1" and the maximum to "12", this task will auto-tag customers who've made at least 1 purchase, and will *remove* the tag when the 13th purchase is made.

## Default options

```json
{
  "purchase_minimum__number_required": "",
  "purchase_maximum__number_required": "",
  "evaluate_purchase_thresholds_by_number_of_orders__boolean": true,
  "evaluate_purchase_thresholds_by_adding_line_item_quantities__boolean": false,
  "evaluate_purchase_thresholds_by_adding_line_item_subtotals__boolean": false,
  "only_count_paid_orders__boolean": false,
  "only_count_this_product_id__number": "",
  "customer_tag_to_apply__required": ""
}
```

## Subscriptions

```liquid
{% if options.only_count_paid_orders__boolean %}
  shopify/orders/paid
{% else %}
  shopify/orders/create
{% endif %}

shopify/orders/cancelled
```

## Documentation

Use this task to auto-tag customers when their historical purchase total falls within a certain range. For example, by configuring this task to evaluate purchase thresholds by number of orders, and by setting the minimum to "1" and the maximum to "12", this task will auto-tag customers who've made at least 1 purchase, and will *remove* the tag when the 13th purchase is made.

Use this task to auto-tag customers when their historical purchase total falls within a certain range. 

For example, by configuring this task to evaluate purchase thresholds by number of orders, and by setting the minimum to "1" and the maximum to "12", this task will auto-tag customers who've made at least 1 purchase, and will *remove* the tag when the 13th purchase is made.

This task can total up purchases by number of orders, adding line item quantities, or by adding line item subtotals. Optionally, choose a specific product ID to filter by. [Learn how to find a product ID](https://help.usemechanic.com/en/articles/2946120-how-do-i-find-an-id-for-a-product-collection-order-or-something-else)

This task will run whenever a new order is created (or paid, if you choose to only count paid orders), and whenever an order is cancelled.
