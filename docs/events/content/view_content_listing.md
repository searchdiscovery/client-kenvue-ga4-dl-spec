---
title: View Content Listing
---

# View Content Listing

Fire whenever a content listing (e.g. Article Card Section, Article List View, etc.) appears on a page.

Pairs with the following event:
- [Select Content](../../events/content/select_content.md)


## Javascript Code

```js
// When:
// User views a listing of articles, article cards, etc.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "view_content_list",
  event_data: {
    list_type: "<list_type>", // REQUIRED | string | ex. cards, search_results	
    identifier: "<identifier>", // REQUIRED | string | ex. ecp_locator, free_trial
    name: "<name>", // REQUIRED | string | ex. purchase_product
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**list_type**|`string`|required|The type of list the item was found in.|`cards, search_results`|`100`|
|**identifier**|`string`|required|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`ecp_locator, free_trial`|`100`|
|**name**|`string`|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`purchase_product`|`100`|
