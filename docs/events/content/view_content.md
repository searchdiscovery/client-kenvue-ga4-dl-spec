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
    identifier: "<identifier>", // recommended | string | ex. ecp_locator, free_trial
    name: "<name>", // REQUIRED | string | ex. purchase_product
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|**content_type**|`string`|recommended|The type of content presented to the user. Use "page" if no more specific `content_type` applies or if the capability to distinguish between content_types does not currenly exist.|`"article"`, `"blog"`|
|**identifier**|`string`|recommended|The content machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`"oral_care"`|
|**name**|`string`|Yes|The content human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`"oral_care"`|
