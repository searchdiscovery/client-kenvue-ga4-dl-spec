---
title: iFrame message
---

# iFrame message

Fire whenever an iframe emits a message using the `window.postMessage` method. 

This will be automatically collected and fired through GTM for now, but the HTML data attributes should still be added if possible to help with identification.

## HTML Data Attributes

```html
<iframe src="<page_location>"
  data-layer-identifier="<identifier>"
  data-layer-name="<name>"
  data-layer-category="<category>"
  data-layer-category2="<category2>"
  data-layer-page_hostname="<page_hostname>"
  data-layer-page_location="<page_location>"
>
```

## Javascript Code

```js
// When:
// Iframe emits a message using window.postMessage method

// Code
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'iframe_post_message',
  event_data: {
    identifier: "<identifier>", // REQUIRED | string | ex. vidyard-video-embed
    name: "<name>", // REQUIRED | string | ex. vidyard video embed
    category: "<category>", // contextual | string | ex. audio, where to buy, video
    category2: "<category2>", // contextual | string | ex. audio, where to buy, video
    data: "<data>", // REQUIRED | variable | ex. {event: 'play', videoName: 'my video', videoProvider: 'vimeo'}
    html_id: "<id>", // contextual | string | ex. hero-video
    html_classes: "<classes>", // contextual | string | ex. audio-embed
    html_element: "<element>", // REQUIRED | HTMLIFrameElement | ex. <iframe src="sample.com/iframe" ...>
    page_hostname: "<page_hostname>", // REQUIRED | string | ex. vimeo.com
    page_location: "<page_location>", // REQUIRED | string | ex. https://www.example.com
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|contextual|An ID added to the iframe via data attributes that can be used to identify which iframe sent the message|`vidyard-video-embed`|`100`|
|**name**|`string`|contextual|A name added to the iframe via data attributes that can be used to identify which iframe sent the message|`vidyard video embed`|`100`|
|**category**|`string`|recommended|A category added to the iframe via data attributes that can be used to represent what type of component/tool/widget is embedded via the iframe|`audio`, `where to buy`, `video`|`100`|
|**category2**|`string`|contextual|Categories 2 - 5 can be used to further categorize the iframe|audio, where to buy, video|
|**data**|variable|required|The data payload sent from the iframe|`{event: 'play', videoName: 'this is a video', videoProvider: 'vimeo'}`|
|**html_id**|`string`|contextual|The iFrame HTML ID attribute.|`hero-video`|`100`|
|**html_classes**|`string`|contextual|The iFrame CSS classes.|`audio-embed`|`100`|
|**html_element**|[HTMLIFrameElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLIFrameElement)|required|The iFrame HTML element.|`<iframe src="neutrogena.com/iframe" ...>`|`100`|
|**page_hostname**|`string`|required|The hostname of the iFrame source.|`vimeo.com`|`100`|
|**page_location**|`string`|required|The full URL of the iFrame source.|`where-to-buy.co/example`|`100`|
