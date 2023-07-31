---
title: View Content
---

# View Content

Fire whenever a page whose main purpose is to serve content (e.g. an article or blog post) loads.

## Javascript Code

```js
// When:
// User views an article, blog post, or other content-focused page

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "view_content",
  event_data: {
    content_type: "<content_type>", // recommended | string | ex. article, blog, page	
    facets: "<facets>", // optional | string - double delimited (:)(~) | category:skin_health~featured_as:best_seller	
    identifier: "<identifier>", // recommended | string | ex. ecp_locator, free_trial
    name: "<name>", // REQUIRED | string | ex. purchase_product
    search_term: "<search_term>", // optional | string | ex. sunscreen
    search_type: "<search_type>", // optional | string | site, filter_by_group	
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|**content_type**|`string`|recommended|The type of content selected by the user. Use "page" if no more specific content_type applies or if the capability to distinguish between content_types does not currenly exist.|article, blog, page|
|**facets**|`string`|contextual|A double-delimited string of key/value pairs representing the refinements that were applied to this search. Only set if the list type is a search result or filter_by_group.|category:skin_health~skin_concern:acne~featured_as:best_seller|
|**identifier**|`string`|recommended|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|ecp_locator, free_trial|
|**name**|`string`|Yes|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.||
|**search_term**|`string`|contextual|The final search term submitted after any correction has been performed. Only set if the `list_type` is `search_results`.|sunscreen|
|**search_type**|`string`|contextual|The type of search performed. Only set if the `list_type` is `search_results`.|site, filter_by_group|
