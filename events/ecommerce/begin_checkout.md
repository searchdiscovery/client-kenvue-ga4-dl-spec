# Begin Checkout

Fire whenever a user begins a checkout. This event is not the same as the ecommerce event "[View Cart](/events/ecommerce/view_cart.md)". This event will fire once the user initiates the checkout funnel. Examples of where the "begin_checkout" event should fire are (but only ONCE during checkout and will be the FIRST thing that fires):
- The user views the form to fill out shipping information
- The user views the form to fill out payment information
- the user view the screen to either log in or create an account to proceed with their checkout


## Javascript Code

```js
// When:
// User begins a checkout

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "begin_checkout",
  ecommerce: {
    coupon: "<coupon>", // contextual | string | ex. SUMMER_FUN | pattern: ^[A-Za-z0-9_]+$
    currency: "<currency>", // REQUIRED | string | ex. USD | pattern: ^[A-Z]{3}$ | min. 3| max. 3
    items: "<items>", // REQUIRED | array | ex. [{item_id: "test"}]
    value: "<value>" // REQUIRED | number | ex. 7.77 | pattern: ^\d\.\d\d$ | min. 0.00
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Minimum Length|Maximum Length|Minimum|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | 
|coupon|string|contextual|The coupon name/code associated with the event. Event-level and item-level coupon parameters are independent.|`SUMMER_FUN`|`^[A-Za-z0-9_]+$`
|currency|string|required|Currency of the items associated with the event, in 3-letter ISO 4217 format.|`USD`|`^[A-Z]{3}$`|`3`|`3`|
|items|array of [items](/schemas/item.md)|required|Populate with item objects that represent the product(s) currently in the cart during the checkout process.|`[{item_id: "test"}]`
|value|number|required|The monetary value of the event. Does not include currency sign.|`7.77`|`^\d\.\d\d$`||`100`|`0.00`|
