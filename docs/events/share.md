# Share

Fire whenever a user shares content via email or social. 

The parameters `page_title` and `page_location` are automatically sent along on each page view and should be able to contextualize this event without any additional information being needed.

???+ info "`item_` parameters in the below schema are NOT the same as `item_` parameters found in the [ecommerce items](../../schemas/item.md) schmea."

    The parameters found in this event are for event collection only and will not impact ecommerce-related events, dimensions, or metrics. 

## HTML Data Attributes

```html
<a href="<link_url>"
  data-layer-event="share"
  data-layer-content_type="<content_type>"
  data-layer-item_id="<item_id>"
  data-layer-method="<method>"
>
```

## Javascript Code

```js
// When:
// User shares to social media.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'share',
  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. contact, lead_generation
    name: '<name>', // REQUIRED | string | ex. contact, lead_generation	
    content_type: '<content_type>', // REQUIRED | string | type of content | ex. blog, landing, content, product, video
    item_brand: "<item_brand>", // contextual | string | ex. tylenol, zyrtec, listerine
    item_id: "<item_id>", // contextual | string | ex. CW21001
    item_name: "<item_name>", // contextual | string | ex. essential_foaming_cleanser 
    item_upc: "<item_upc>", // contextual | string | ex. 012345678905 (12 digits)
    link_url: "<link_url>" // contextual | string | ex. https://www.example.com/?q=product#id
    method: '<method>' // REQUIRED | string | social platform | ex. email, facebook, twitter
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The shared content machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`contact`, `lead_generation`|`100`|
|**name**|`string`|required|The shared content human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the event with. It should be lowercase snake_case.|`contact`, `lead_generation`|`100`|
|**content_type**|`string`|required|The type of content shared.|`blog`, `content`, `home`, `landing`, `product`, `video`, `livestream event`|`100`|
|**item_brand**|`string`|required|The human-readable name of the brand. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`tylenol`, `zyrtec`, `listerine`|`100`|
|**item_id**|`string`|required|SKU ID of the product a customer is sharing.|`CW21001`|`100`|
|**item_name**|`string`|required|The human-readable product name of the product a customer is sharing. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case|`essential_foaming_cleanser`|`100`|
|**item_upc**|`string`|contextual|UPC ID of the product a customer is sharing.|`012345678905`|`100`|
|**link_url**|`string`|required|The full URL of the object.|`https://www.example.com?q=product#id`|`100`|
|**method**|`string`|required|The platform used to share content|`email`, `facebook`, `twitter`|`100`|
