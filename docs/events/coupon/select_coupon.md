# Select Coupon

Fire whenever a user selects a coupon.

## Javascript Code

```js
// When:
// User selects a coupon

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'select_coupon',
  event_data: {
    coupons: '<coupons>', // REQUIRED | string - delimited (~) | ex. couponName1~couponName2~couponName3
    identifier: '<identifier>', // recommended | string | ex. neutrogena_discount, free_shipping_q421
    name: '<name>', // REQUIRED | string | ex. neutrogena_discount, free_shipping_q421
    type: '<type>' // REQUIRED | string | ex. discount, promo
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|**coupons**|`delimited string`|required|A delimited string of coupons that the user selected and is now downloading or printing.|`couponName1~couponName2~couponName3`|`100`|
|**identifier**|`string`|required|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`neutrogena_discount`, `free_shipping_q421`|
|**name**|`string`|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`neutrogena_discount`, `free_shipping_q421`|
|**type**|`string`|required|The coupon type. This will act as a filtering mechanism in reporting to enable analysts to view coupon engagement. It can also act as an internal aid in firing additional events if necessary.|`discount`, `promo`|
