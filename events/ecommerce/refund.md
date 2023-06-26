# Refund

Fire whenever a refund is issued. The Google Analytics 4 schema has some very extreme requirements about what is needed to be recognized as a true refund/transaction. The following parameters are _**100% REQUIRED**_ when implementing the refund event for a _**PARTIAL REFUND**_:

- Transaction ID (transaction_id)
- Currency (currency)
- Value (value)
- Items (items

The following parameters are _**100% REQUIRED**_ when implementing the refund event for a _**FULL REFUND**_:

- Transaction ID (transaction_id)
- Currency (currency)
- Value (value)

You may notice the "[item Array](/schemas/item.md)" is not present in the _**FULL REFUND**_ events like it is the _**PARTIAL REFUND**_ event and the "[Purchase Event](/events/ecommerce/purchase.md)", this is because when performing a _**FULL REFUND**_ GA4 will assume all products have been returned.

## Javascript Code

```js
// When:
// User refund is issued

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "refund",
  ecommerce: {
    affiliation: "<affiliation>", // REQUIRED | string | ex. walgreens, listerine online store |
    coupon: "<coupon>", // contextual | string | ex. SUMMER_FUN |
    currency: "<currency>", // REQUIRED | string | ex. USD | pattern: ^[A-Z]{3}$ | min. 3, max. 3
    items: "<items>", // REQUIRED | array | ex. [{item_id: "test"}]
    shipping: "<shipping>", // REQUIRED | number | ex. 3.33 | pattern: ^\d\.\d\d$	| min. 0.00
    tax: "<tax>", // REQUIRED | number | ex. 1.11 | pattern: ^\d\.\d\d$	| min. 0.00
    transaction_id: "<transaction_id>", // REQUIRED | string | ex. T12345
    quantity: "<quantity>", // REQUIRED | number | ex. 3
    value: "<value>" // REQUIRED | number | ex. 7.77 | pattern: ^\d\.\d\d$ | min. 0.00
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Minimum Length|Maximum Length|Minimum|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|affiliation|string|required|A product affiliation to designate a supplying company or brick and mortar store location. Event-level and item-level affiliation parameters are independent.|`walgreens`,`listerine online store`|||`100`|
|coupon|string|contextual|The coupon name/code associated with the event. Event-level and item-level coupon parameters are independent.|`SUMMER_FUN`|||`100`|
|currency|string|required|Currency of the items associated with the event, in 3-letter ISO 4217 format.|`USD`|`^[A-Z]{3}$`|`3`|`3`|
|items|array of [items](/schemas/item.md)|required|Populate with item objects that represent the product(s) returned. Note that **items** is required for partial refunds but it can be omitted for full refunds.|`[{item_id: "test"}]`
|shipping|number|required|Shipping cost associated with a transaction. Does not include currency sign.|`3.33`|`^\d\.\d\d$`||`100`|`0.00`|
|tax|number|required|Tax cost associated with a transaction. Does not include currency sign.|`1.11`|`^\d\.\d\d$`||`100`|`0.00`|
|transaction_id|string|required|The unique identifier of a transaction.|`T12345`|||`100`|
|quantity|number|required|the number of items.||||`100`
|value|number|required|The monetary value of the event. Does not include currency sign.|`7.77`|`^\d\.\d\d$`||`100`|`0.00`|
