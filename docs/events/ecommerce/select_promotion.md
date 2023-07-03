# Select Promotion

Fire whenever a user clicks on a promotion link located in a component that forwards the user to a promotional page or an item/product. Component types include cards, carousels, search, promotions, home screen hero images, and similar components. A promotion is usually a temporary presentation of information that is different than displaying a dynamic list which would normally send a [View Item List](/events/ecommerce/view_item_list.md).

The most common use case of the "select_promotion" event is a hero image that is displayed on the home page of a brand site as this is most commonly a promotion space that will drive a user to a product or product list.

Pairs with "[View Promotion](/events/ecommerce/view_promotion.md)".

## Javascript Code

```js
// When:
// User user clicks on a promotion link found in the promotion component (cards, carousels, search, promotions, home screen hero images) that forwards to a promotional page or an item/product

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "select_promotion",
  ecommerce: {
    creative_name: "<creative_name>", // REQUIRED | string | ex. summer_banner2	
    creative_slot: "<creative_slot>", // REQUIRED | string | ex. featured_hero_splash_1	
    promotion_id: "<promotion_id>", // REQUIRED | string | ex. P_12345
    promotion_name: "<promotion_name>", // REQUIRED | string | summer_sale_2023
    items: "<items>" // REQUIRED | array | ex. [{item_id: "test"}]
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Max Length|
| --- | --- | --- | --- | --- | --- |
|creative_name|string|required|The name of the promotional creative. Ignored if set at the item-level.|`summer_banner2`|`100`|
|creative_slot|string|required|The name of the promotional creative slot associated with the event. Ignored if set at the item-level.|`featured_hero_splash_1`|`100`|
|promotion_id|string|required|The ID of the promotion associated with the event. Ignored if set at the item-level.|`P_12345`|`100`|
|promotion_name|string|required|The name of the promotion associated with the event. Ignored if set at the item-level.|`summer_sale_2023`|`100`|
|items|array of [items](../../schemas/item.md)|required|Populate with item objects that represent the product viewed.|`[{item_id: "test"}]`|
