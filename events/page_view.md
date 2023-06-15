# Page View

Fire whenever a user loads in a new page, whether that is done synchronously or asynchronously.

This event should be the first pushed into the data layer on each page. Given many 3rd party scripts push events to the data layer, this event push should be placed in the page `<head>` and should be the first `<script>` tag on the page to ensure it is the first event.

There is no longer a concept of virtual page view, so this event should be fired whenever a virtual page view would have been fired in the past, such as when a new screen is loaded asyncronously within an angular, react, or vue app/embed.

## Javascript Code

```js
// When:
// User loads a new page (synchronously or asynchronously)
// Should be the first push into dataLayer, placed in the <head> and ideally first <script> on page.

// Code
window.dataLayer = window.dataLayer || [];
dataLayer.push({ page_data: null, user_data: null });  // Clear the previous attributes.
dataLayer.push({
  event: 'page_view',
  page_data: {
    page_category: '<category>', // REQUIRED | string | ex. sun protection
    page_subcategory: '<page_subcategory>', // recommended | string | ex. waterproof
    page_id: '<page_id>', // REQUIRED | string | ex. 12345
    page_location: '<page_location>', // REQUIRED | string | ex. https://www.example.com
    page_name: '<page_name>', // REQUIRED | string | ex. homepage, search results, product:sample
    page_type: '<page_type>', // REQUIRED | string | ex. article, blog, homepage, product
    site_brand: '<site_brand>', // REQUIRED | string | ex. neutrogena
    site_country: '<site_country>', // REQUIRED | string | ex us, au, is, jp
    site_region: '<site_region>', // REQUIRED | string | ex. EMEA
    site_section: '<site_section>', // REQUIRED | string | ex. products
    user_login_state: '<user_login_state>' // REQUIRED | string | ex. authenticated, anonymous 
  },
  user_data: {
    user_id: '<user_id>' // REQUIRED, if user is logged in | string | ex. 12345
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|site_brand|string|required|The brand the site is associated with.|neutrogena|
|site_country|string|required|The country the site is associated with.|us|
|page_category|string|required|Used for grouping pages (or screens) into categories based on their content. Most often aligns with page tags/taxonomy terms or breadcrumbs.|sun protection|
|page_subcategory|string|recommended|Used for grouping pages (or screens) into subcategories based on their content. Most often aligns with page tags/taxonomy terms or breadcrumbs.|waterproof|
|page_id|string|required|A durable identifier for a page that will enable measurement over time despite the page URL, title, etc changing. Generally sourced from the site content management system.|12345|
|page_location|string|required|The url of the page currently being viewed.|https://www.neutrogena.com|
|page_name|string|required|A unique name for this page independent of page title. Google does not tend to use custom page names, but it's a mainstay in Adobe and therefore is included here for compatibility as well as for its usefulness generally.|homepage,search results,product:neutrogena hydro boost gel|
|page_type|string|required|Used for grouping pages (or screens) into high level types.|article,blog,homepage,product|
|site_region|string|required|The region the site is associated with.|EMEA|
|site_section|string|required|The section of the site that the current page resides in.|products|
|user_id|string|contextual|The id of the user currently logged in to the site, if the site offers authentication and the user is authenticated.|123456|
|user_login_state|string|contextual|Set on all events with the authentication status of the visitor.|authenticated, anonymous|
