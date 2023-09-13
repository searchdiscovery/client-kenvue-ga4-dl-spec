---
title: Form Start
---

# Form Start

Fire whenever a user starts filling out a form. 

This event is generally fired after user input in the first form field. Historically this has been done via an HTMLElement change event on a form field, though it could be done via an HTMLElement focus event on a form field instead if that proves easier to implement. It should only be fired once per form, but if that is too technically complicated to implement, it can be limited on the GTM side instead.


## Javascript Code

```js
// When:
// User starts to fill out a form. The event fires after user input into the first form field 
// and should only fire once. onchange(), onfocus(), and GTM may be helpful.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'form_start',
  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. ecp_locator, free_trial	
    name: '<name>', // REQUIRED | string | ex. ecp_locator, free_trial	
    type: '<type>', // REQUIRED | string | ex. contact, lead_generation
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`contact`, `lead_generation`|`100`|
|**name**|`string`|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`contact`, `lead_generation`|`100`|
|**type**|`string`|required|The form type. This will act as a filtering mechanism in reporting to enable analysts to view form droppoff funnels. It can also act as an internal aid in firing additional events if necessary. For instance, lead-generating forms require a `generate_lead` event to be fired alongside `form_complete`, and that could be written into the logic based upon this field.|`contact`, `lead_generation`|`100`|
