# View Search Results

Fire whenever a user views search results. This includes product searches, content searches, resource searches, etc., and **_DOES NOT REQUIRE_** a search event to be fired prior to it.

This event should also be considered for the "Filter By Group" component if it is ever used to display anything but products. When used in this way, the search_term parameter would be `filter_by_group` as that component does not currently allow for a search_term to be entered by the user. If this case does arise, contact Search Discovery for additional information.
## Javascript Code

```js
// When:
// User views search results and does not require a search event to be fired previously

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "view_search_results",
  event_data: {
    facets: "<refinements>", // contextual | string - double delimited (:)(~) | ex. category:skin_health~featured_as:best_seller	
    number_of_items: "<number_of_items>", // REQUIRED | integer | ex. 1,324,0
    search_term: "<search_term>", // REQUIRED | string | ex. sunscreen
    search_type: "<search_type>", // REQUIRED | string | ex. ecp_locator, filter_by_group,product, site	
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|`facets`|delimited string|contextual|A delimited string of key/value pairs representing the facets that were applied to this search|`need:skin health~skin_concern:acne~featured_as:best_seller`|`100`|
|`number_of_items`|integer|required|The total number of search results found|`1`,`324`.`0`|`100`|
|`search_term`|string|required|The final search term submitted after any correction has been performed|`sunscreen`|`100`|
|`search_type`|string|required|The type of search performed|`ecp_locator`,`filter_by_group`,`product`,`site`|`100`|
