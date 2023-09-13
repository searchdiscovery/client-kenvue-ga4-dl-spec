---
title: Form File Uploaded
---

# Form File Uploaded

Fire whenever a user successfully uploads a file (such as a receipt) within a form.


## Javascript Code

```js
// When:
// User successfully uploads a file (like a receipt) within a form.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null, user_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'form_file_upload',
  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. ecp_locator, free_trial	
    name: '<name>', // REQUIRED | string | ex. ecp_locator, free_trial	
    type: '<type>', // REQUIRED | string | ex. contact, lead_generation
    file_extension: '<file_extension>', // REQUIRED | string | ex. pdf
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`contact`, `lead_generation`|`100`|
|**name**|`string`|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`contact`, `lead_generation`|`100`|
|**type**|`string`|required|The form type. This will act as a filtering mechanism in reporting to enable analysts to view form droppoff funnels. It can also act as an internal aid in firing additional events if necessary. For instance, lead-generating forms require a `generate_lead` event to be fired alongside `form_complete`, and that could be written into the logic based upon this field.|`contact`, `lead_generation`|`100`|
|**file_extension**|`string`|REQUIRED|The file extension of the file being uploaded.|`pdf`|`100`|
