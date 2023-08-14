# Item Object

An `item` is how GA4 refers to a product.  An item object should be sent whenever a product is displayed, selected, added to a cart, or purchased.

## Object format

```json
{
  // Global
  "affiliation": "<affiliation>",
  "currency": "<currency>",
  "gtin": "<gtin>",
  "item_brand": "<item_brand>",
  "item_category": "<item_category>",
  "item_id": "<item_id>",
  "item_name": "<item_name>",
  "item_need_state": "<item_need_state>",
  "item_subcategory": "<item_subcategory>",
  "item_subsegment": "<item_subsegment>",
  "item_upc": "<item_upc>",
  "item_variant": "<item_variant>",
  "price": "<price>",
  "quantity": "<quantity>",
  "sku": "<sku>",

  // Contextual
  "coupon": "<coupon>",
  "discount": "<discount>",
  "creative_name": "<creative_name>",
  "creative_slot": "<creative_slot>",
  "index": "<index>",
  "item_list_id": "<item_list_id>",
  "item_list_name": "<item_list_name>",
  "item_out_of_stock": "<item_out_of_stock>",
  "item_subscription_type": "<promotion_id>",
  "location_id": "<location_id>",
  "promotion_id": "<promotion_id>",
  "promotion_name": "<promotion_name>"
}
```

## Variable definitions
|Name|Type|Required|Description|Example Value|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|`affiliation`|string|required|A product affiliation to designate a supplying company or brick and mortar store location.|`Google Store`|100|
|`coupon`|string|contextual|Coupon code used for a purchase.|`SUMMER_FUN`|100|
|`creative_name`|string|required if item is being sent with a promotion event|The name of a creative used in a promotional spot.|`summer_banner2`|100|
|`creative_slot`|string|required if item is being sent with a promotion event|The name of a creative slot.|`featured_app_1`|100|
|`currency`|string|required|The currency, in 3-letter ISO 4217 format.|`USD`|100|
|`discount`|number|contextual|Monetary value of discount associated with a purchase.|`2.22`|100|
|`gtin`|string|required|A Global Trade Item Number (GTIN). GTINs identify trade items, including products and services, using numeric identification codes. UPCs are a type of GTIN, so they should be added via this parameter.|`012345678905`|
|`index`|number|contextual|The index/position of the item in a list.|`2`|100|
|`item_brand`|string|required|Item brand|`Gucci`|100|
|`item_category`|string|required|Item Category (context-specific).|`pants`|100|
|`item_id`|string|required|Item ID (context-specific). `item_id` should be the item's UPC code, if available. If UPC is not available, `item_id` should be the item's SKU ID. If neither UPC nor SKU are available, the value should be an empty string.|`UPC12345`, `SKU12345`, `""`|100|
|`item_list_id`|string|contextual|The computer-readable machine name of the list the item showed up in (if sent with a view_item_list event). Use UUID provided by the component if no more specific ID is available.|`12345abcde12345`|100|
|`item_list_name`|string|contextual|The human-readable name of the item list the item showed up in (if sent with a view_item_list event). If one is not available, populate with numerical index of which list this is on the page (1-indexed). For `filter_by_group` component, use that value.|`filter_by_group`, `recommended_products`, `recently_viewed_products`|100|
|`item_name`|string|required|Item Name (context-specific).|`jeggings`|100|
|`item_need_state`|string|required|Item Need State (context-specific).|`**NEED EXAMPLES FROM STEVEN FOR DOCUMENTATION**`|100|
|`item_out_of_stock`|string|contextual|Send as true if an item is out of stock. You should exclude this parameter if the item is in stock.|`true`|100|
|`item_subcategory`|string|required|Item Sub-Category (context-specific).|`facial moisturizers & serums`, `best sellers`, `new`|100|
|`item_subsegment`|string|required|Item Sub-Segment (context-specific).|`**NEED EXAMPLES FROM STEVEN FOR DOCUMENTATION**`|100|
|`item_subscription_type`|string|contextual|Item Subscription Type. The subscription type when a user chooses to subscribe to a product being sent multiple times after their purchase.|`3-months`, `6-months`, `9-months`|100|
|`item_upc`|string|contextual|UPC ID of the product a customer would be calling a store about.|`012345678905`|100|
|`item_variant`|string|required|The variant of the item.|`Black`|100|
|`location_id`|string|required if the item is associated with a physical location|The location associated with the event. If possible, set to the Google Place ID that corresponds to the associated item. Can also be overridden to a custom location ID string.|`L_12345`|100|
|`price`|number|required|The monetary price of the item, in units of the specified currency parameter.|`9.99`|100|
|`promotion_id`|string|required if item is being sent with a promotion event|The ID of a product promotion. |`P_12345`|100|
|`promotion_name`|string|required if item is being sent with a promotion event|The name of a product promotion. One of `promotion_id` or `promotion name` is required.|`Summer Sale`|100|
|`quantity`|integer|required|Item quantity.|`1`|100|
|`sku`|string|contextual|The item's stock-keeping unit (SKU) ID, when available.|`SKU12345`|100|
