# View Cart

Fire whenever a user views their cart. This event is not the same as the ecommerce event "[Begin Checkout](/events/ecommerce/begin_checkout.md)". Unlike "[Begin Checkout](/events/ecommerce/begin_checkout.md)", the view_cart event will fire when a user is preparing to finalize their purchase, usually presented with their list of products, as well as options as to how they will proceed with checking out (e.g. normal checkout, paypal, amazon, etc). 

## Javascript Code

```js
// When:
// User views cart

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_cart",
  ecommerce: {
    currency: "<currency>", // REQUIRED | string | ex. USD | pattern: ^[A-Z]{3}$ | min. 3, max. 3
    items: "<items>", // REQUIRED | array | ex. [{item_id: "test"}]
    value: "<value>" // REQUIRED | number | ex. 7.77 | pattern: ^\d\.\d\d$ | min. 0.00
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Minimum Length|Maximum Length|Minimum|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|currency|string|required|Currency of the items associated with the event, in 3-letter ISO 4217 format.|`USD`|`^[A-Z]{3}$`|`3`|`3`|
|items|array of [items](/docs/schemas/item.md)|required|Populate with item objects that represent the product viewed.|`[{item_id: "test"}]`|||`100`|
|value|number|required|The monetary value of the event. Does not include currency sign.|`7.77`|`^\d\.\d\d$`||`100`|`0.00`|
