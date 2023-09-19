---
title: Change Item SKU
---

# Close WTB Widget

Fire whenever a user successfully closes the WTb widget. 

## Javascript Code

```js
// When:
// User successfully closes the WTB tool.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null});  // Clear the previous event_data object.
dataLayer.push({
  event: "widget_closed_wtb"  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. contact, lead_generation
    name: '<name>', // REQUIRED | string | ex. contact, lead_generation	
    affiliation: "<affiliation>", // REQUIRED | string | ex. walmart, cvs
    component_type: "<component_type>", // REQUIRED | string | ex. pricespider, channeladvisor
    item_brand: "<item_brand>", // REQUIRED | string | ex. tylenol, zyrtec, listerine
    item_id: "<item_id>", // REQUIRED | string | ex. CW21001
    item_name: "<item_name>", // REQUIRED | string | ex. essential_foaming_cleanser 
    item_upc: "<item_upc>", // contextual | string | ex. 012345678905 (12 digits)
    link_url: "<link_url>" // REQUIRED | string | ex. https://www.example.com/?q=product#id
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
|**item_id**|`string`|required|SKU ID of the product a customer would be calling a store about.|`CW21001`|`100`|
|**item_name**|`string`|required|The human-readable product name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`essential_foaming_cleanser`|`100`|
|**item_upc**|`string`|contextual|UPC ID of the product a customer would be calling a store about.|`012345678905`|`100`|
|**link_url**|`string`|required|This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`https://www.example.com?q=product#id`|`100`|
