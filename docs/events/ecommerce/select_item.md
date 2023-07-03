# Select Item

Fire whenever a user clicks on a product link found in a list that forwards the user to the product detail page. List types include cards, search, promotions, and similar component.

If the site is not currently able to support differentiating products from content, then add the attributes/event for **[select_content](/events/lists/select_content.md)** instead and add a dev task to update the site to enable this differentiation.

Do not fire this event for product links found in menus.

## Javascript Code

```js
// When:
// User clicks on a product link in a list (cards, search, promotions...) that forwards to a product detail page. 
// Do not use this event for product links found in menus.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "select_item",
  ecommerce: {
    facets: "<facets>", // contextual | string - double delimited (:)(~) | category:skin_health~featured_as:best_seller	
    items: "<items>", // REQUIRED | array | ex. [{item_id: "070501110485", item_name: "Neutrogena Hydro Boost Gel-Cream"}]	
    item_list_id: "<item_list_id>", // REQUIRED | string | ex. 12345abcde12345
    item_list_name: "<item_list_name>", // REQUIRED | string | ex. filter_by_group, recommended_products, recently_viewed_products
    list_type: "<list_type>", // REQUIRED | string | ex. cards, search_results	
    search_term: "<search_term>", // contextual | string | ex. sunscreen
    search_type: "<search_type>", // contextual | string | ex. site, filter_by_group
    index: "<index>", // REQUIRED | integer | ex. 5
  }
});
```

## Variable Definitions
|Field|Type|Required|Description |Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|facets|delimited string|contextual|A double-delimited string of key/value pairs representing the refinements that were applied to this search. Only set if the list type is a search result or filter_by_group.|`category:skin_health\~skin_concern:acne\ ~featured_as:best_seller`|`100`|
|items|array of [items](../../schemas/item.md)|required|Populate with only the item that was selected. This should always be a single item array.|`[{item_id: "070501110485", item_name: "Neutrogena Hydro Boost Gel-Cream with Hyaluronic Acid for Extra-Dry Skin"}]`|
|item_list_id|string|required|The computer-readable machine name of the list the item showed up in. Use UUID provided by the component if no more specific ID is available.|`12345abcde12345`|`100`|
|item_list_name|string|required|The human-readable name of the list the item showed up in. If one is not available, populate with numerical index of which list this is on the page (1-indexed). For `filter_by_group` component, use that value.|`filter_by_group, recommended_products, recently_viewed_products`|`100`|
|list_type|string|required|The type of list the item was found in.|`cards, search_results`|`100`|
|search_term|string|contextual|The final search term submitted after any correction has been performed. Only set if the `list_type` is `search_results`.|`sunscreen`|`100`|
|search_type|string|contextual|The type of search performed. Only set if the `list_type` is `search_results`.|`site, filter_by_group`|`100`|
|index|integer|required|The numerical index of the item position (1-indexed). For instance, if this is the 5th search result, you would send 5 here. If this is the 3rd card in a single row, send 3. If this is the 2nd item in the 3rd row of a 3-up card layout, send 8 (3 + 3 + 2).|`5`|`100`|
