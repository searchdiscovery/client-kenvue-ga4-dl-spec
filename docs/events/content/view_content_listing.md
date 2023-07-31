---
title: View Content Listing
---

# View Content Listing

Fire whenever a content listing (e.g. Article Card Section, Article List View, etc.) appears on a page.

## Javascript Code

```js
// When:
// User views an article, blog post, or other content-focused page

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "view_content_list",
  event_data: {
    content_list_type: "<content_type>", // recommended | string | e.g. "article_card_section", "article_list_view"
    identifier: "<identifier>", // recommended | string | e.g. "featured_articles", "oral_care"
    name: "<name>", // REQUIRED | string | e.g. "Featured Articles", "Oral Care"
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|**content_list_type**|`string`|recommended|The type of content selected by the user. Use "page" if no more specific content_type applies or if the capability to distinguish between content_types does not currenly exist.|article, blog, page|
|**identifier**|`string`|recommended|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|ecp_locator, free_trial|
|**name**|`string`|Yes|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.||
