---
title: View Content
---

# View Content

Fire whenever a page whose main purpose is to serve content (e.g. an article or blog post) loads.

This event is to be used to understand when content is being viewed without any association to a "[Content List](../../events/content/view_content_listing.md)".

??? info "How this event data is used in reporting"
    
    If an analyst is looking to report on how often a piece of content was engaged with and wants to know the list information (as opposed to how often a content page was viewed), they would use the "[select_content](../../events/content/view_content_listing.md)" in a GA4 report (as opposed to "view_content"). This is because "view_content" will not have associated list information.

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
    content_type: "<content_type>", // REQUIRED | string | ex. article, blog, page		
    identifier: "<identifier>", // REQUIRED | string | ex. ecp_locator, free_trial
    name: "<name>", // REQUIRED | string | ex. purchase_product
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**content_type**|`string`|required|The type of content selected by the user. Use "page" if no more specific content_type applies or if the capability to distinguish between content_types does not currenly exist.|`article, blog, page`|`100`|
|**identifier**|`string`|required|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`ecp_locator, free_trial`|`100`|
|**name**|`string`|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`purchase_product`|`100`|
