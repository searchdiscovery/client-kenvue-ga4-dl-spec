---
title: Video Livestream Start
---

# Video Livestream Start

Fire whenever a user starts a live stream video. This will usually be picked up automatically by GTM on desktop but may need to be manually sent on mobile.

## Javascript Code

```js
// When:
// Video starts, useful for mobile

// Code
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'video_livestream_start',
  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. 2023 My Video For All, 2023 Product Holiday Launch
    name: '<name>', // REQUIRED | string | ex. 2023 My Video For All, 2023 Product Holiday Launch
    type: '<type>', // REQUIRED | string | ex. public, internal, brand awareness, lead_generation
    video_current_time: '<video_current_time>', // REQUIRED | string | ex. 15
    video_duration: '<video_duration>', // REQUIRED | string | ex. 600
    video_percent: '<video_percent>', // REQUIRED | string | ex. 15
    video_provider: '<video_provider>', // REQUIRED | string | ex. youtube, vimeo, firework, twitch
    video_title: '<video_title>', // REQUIRED | string | ex. My Video
    video_url: '<video_url>', // REQUIRED | string | https://youtu.be/12345ABC
    visible: '<visible>', // REQUIRED | boolean | ex. true
  }
});
```
## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The video livestream machine-readable name. This should be a unique value specific to this video livestream, if one exists. If one does not exist, this can also be populated with the same value as the `name`.|`2023 My Video For All`, `2023 Product Holiday Launch`|`100`|
|**name**|`string`|required|The video livestream human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the video livestream with. It should be lowercase snake_case.|`2023 My Video For All`, `2023 Product Holiday Launch`|`100`|
|**type**|`string`|required|The video livestream type. This will act as a filtering mechanism in reporting to enable analysts to view video livestream dropoff funnels. It can also act as an internal aid in firing additional events if necessary. For instance, a lead-generating video livestream requires a `generate_lead` event to be fired alongside `video_livestream_exit`, and that could be written into the logic based upon this field.|`public`,`internal`,`brand awareness`, `lead_generation`|`100`|
|**video_current_time**|`string`|required|The current time of the video viewed.|`15`|`100`|
|**video_duration**|`string`|required|The total duration of the video.|`600`|`100`|
|**video_percent**|`string`|required|The current percent of the video viewed.|`15`|`100`|
|**video_provider**|`string`|required|The video provider.|`youtube`, `vimeo`, `firework`, `twitch`|`100`|
|**video_title**|`string`|required|The title of the video.|`My Video`|`100`|
|**video_url**|`string`|required|The URL of the video.|`https://youtu.be/RhS85WQiBLU`|`100`|
|**visible**|`boolean`|required|Is the video visible on the page.|`true`|`100`|
