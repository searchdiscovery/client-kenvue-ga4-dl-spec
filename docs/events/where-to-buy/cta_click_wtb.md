---
title: Call Click WTB
---

# CTA Click WTB

Fire whenever a user successfully clicks on a WTB CTA link.

This event will be automatically detected and fired if the data attributes below are added to each link (`<a>` tag if possible, but if there is no `<a>` tag then add them to the `<div>` or other tag that represents the link).

???+ info "`item_` parameters in the below schema are NOT the same as `item_` parameters found in the [ecommerce items](../../schemas/item.md) schmea."

    The parameters found in this event are for event collection only and will not impact ecommerce-related events, dimensions, or metrics. 

## HTML Data Attributes

```html
<div
  data-layer-event="cta_click_wtb"
  data-layer-identifier="<identifier>"
  data-layer-name="<name>"
  data-layer-affiliation="<affiliation>"
  data-layer-component_type="<component_type>"
  data-layer-component_type="<item_brand>"
  data-layer-category="<category>"
  data-layer-discount="<discount>"
  data-layer-item_id="<item_id>"
  data-layer-item_name="<item_name>"
  data-layer-link_text="<link_text>"
  data-layer-link_text="<item_upc>"
  data-layer-link_url="<link_url>"
  data-layer-price="<price>"
>
```

## Javascript Code

```js
// When:
// User clicks on a CTA link
// NOTE: Event is automatically fired if the attributes are added to an HTML anchor element
// or HTML element representing a link

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "cta_click_wtb",
  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. contact, lead_generation
    name: '<name>', // REQUIRED | string | ex. contact, lead_generation	
    affiliation: "<affiliation>", //REQUIRED | string | ex. Amazon.com, Walmart.com, CVS
    component_type: "<component_type>", // REQUIRED | string | ex. pricespider, channeladvisor
    item_brand: "<item_brand>", // REQUIRED | string | ex. tylenol, zyrtec, listerine
    category: "<category>", // contextual | string | ex. find online, find locally
    discount: "<discount>", // contextual | number | ex. 2.22
    item_id: "<item_id>", // REQUIRED | string | ex. SKU_12345
    item_name: "<item_name>", // REQUIRED | string | ex. jeggings
    link_text: "<link_text>", // REQUIRED | string | ex. Add to Cart, Buy Now, Get Directions, store hours
    item_upc: "<item_upc>", // contextual | string | ex. 012345678905 (12 digits)
    link_url: "<link_url>", // REQUIRED | string | ex. https://www.example.com/link?test=testing
    price: "<price>", // contextual | string | ex. 9.99
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The wtb-event machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`contact`, `lead_generation`|`100`|
|**name**|`string`|required|The wtb-event human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the event with. It should be lowercase snake_case.|`contact`, `lead_generation`|`100`|
|**affiliation**|`string`|required|This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`walmart`, `cvs`|`100`|
|**component_type**|`string`|required|The human-readable name of the WTB Provider. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case.|`pricespider`, `channeladvisor`|`100`|
|**item_brand**|`string`|required|The human-readable name of the brand. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`tylenol`, `zyrtec`, `listerine`|`100`|
|**category**|`string`|contextual|Used to differentiate buy online versus buy locally.|`find online,find locally`|`100`|
|**discount**|`number`|contextual|Monetary value of discount associated with a purchase.|`2.22`|`100`|
|**item_id**|`string`|required|SKU ID of the product a customer would be calling a store about.|`CW21001`|`100`|
|**item_name**|`string`|required|The human-readable product name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`essential_foaming_cleanser`|`100`|
|**item_upc**|`string`|contextual|UPC ID of the product a customer would be calling a store about.|`012345678905`|`100`|
|**link_url**|`string`|required|This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`https://www.example.com?q=product#id`|`100`|
|**price**|number|contextual|The monetary price of the item, in units of the specified currency parameter.|`9.99`|`100`|
