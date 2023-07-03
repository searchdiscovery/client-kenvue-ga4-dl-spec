# Add Shipping Info

Fire whenever a user submits their shipping information. This event will fire _**AFTER**_ the user has successfully completed the "Add Shipping Info" step and has done the following:

1. Shipping info has populated all required shipping fields.
2. The user has selected to move on to the next step (e.g. payment info, order review, etc.).
3. The system has successfully verified the shipping info and moves the user from the shipping step to the following step.

Pairs with the following events:
- [Begin Checkout](../../events/ecommerce/begin_checkout.md)
- [Add Payment Info](../../events/ecommerce/add_payment_info.md)

## Javascript Code

```js
// When:
// User user submits shipping information

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_shipping_info",
  ecommerce: {
    coupon: "<coupon>", // contextual | string | ex. SUMMER_FUN
    currency: "<currency>", // REQUIRED | string | ex. USD | pattern: ^[A-Z]{3}$ | min. 3, max. 3
    items: "<items>", // REQUIRED | array | ex. [{item_id: "test"}]	
    shipping_tier: "<shipping_tier>", // contextual | string | ex. ground | pattern: ^[a-z_]+$
    value: "<value>" // REQUIRED | number | ex. 7.77 | pattern: ^\d\.\d\d$ | min. 0.00
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Minimum Length|Maximum Length|Minimum|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|coupon|string|contextual|The coupon name/code associated with the event. Event-level and item-level coupon parameters are independent.|`SUMMER_FUN`|||`100`|
|currency|string|required|Currency of the items associated with the event, in 3-letter ISO 4217 format.|`USD`|`^[A-Z]{3}$`|`3`|`3`|
|items|array of [items](../../schemas/item.md)|required|Populate with item objects that represent the product(s) currently in the cart during the checkout process.|`[{item_id: "test"}]`|
|shipping_tier|string|contextual|The shipping method selected for delivery of the purchased item(s).|`ground`|||`100`|
|value|number|required|The monetary value of the event. Does not include currency sign.|`7.77`|`^\d\.\d\d$`||`100`|`0.00`|
