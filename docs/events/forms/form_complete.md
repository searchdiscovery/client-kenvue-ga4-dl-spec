---
title: Form Complete
---

# Form Complete

Fire whenever a user successfully completes a form. 

This event is fired when form input is successfully received and processed. This is in contrast to [`form_error`](../../events/forms/form_error.md) which occurs when a submission is attempted but an error occurs and the form input is not received and processed.

!!! warning

    _**Do not**_ clear the page_data variable before setting user_login_state here as this is not a page view.

??? info "DO NOT populate user_id with a string value if unavailable"

    If the "user_id" is _**NOT**_ available, _**DO NOT**_ populate with an empty string (ex. "") or undefined as a string (ex. "undefined"). This value must _**ONLY**_ be populated with a valid user id. If this value is not available, then either _**DO NOT**_ include the parameter in the data layer push or populate with an undefined object (not a string).

## Javascript Code

```js
// When:
// User successfully completes a form and data is received and processed
// NOTE: Do not clear the page_data variable before setting user_login_state here. This is not a page view.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null, user_data: null });  // Clear the previous event_data and user_data objects.
dataLayer.push({
  event: 'form_complete',
  page_data: {
    user_login_state: '<user_login_state>', // REQUIRED | string | ex. authenticated, anonymous	
  event_data: {
    identifier: '<identifier>', // REQUIRED | string | ex. contact, lead_generation
    name: '<name>', // REQUIRED | string | ex. contact, lead_generation	
    type: '<type>' // REQUIRED | string | ex. contact, lead_generation	
  },
  user_data: {
    user_id: '<user_id>', // contextual | string | ex. 12345
    user_type: '<user_type>' // contextual | string | ex. new, returning
    event_form_custkey: '<SFMC_CustomerKey>', // contextual | string | ex. 12345...
    event_form_hashemail: '<HashedEmail>' // contextual | string | ex. b642b4217b34b1e8d3bd915fc65c4452 (MD5)
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The form machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`contact`, `lead_generation`|`100`|
|**name**|`string`|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|`contact`, `lead_generation`|`100`|
|**type**|`string`|required|The form type. This will act as a filtering mechanism in reporting to enable analysts to view form droppoff funnels. It can also act as an internal aid in firing additional events if necessary. For instance, lead-generating forms require a `generate_lead` event to be fired alongside `form_complete`, and that could be written into the logic based upon this field.|`contact`, `lead_generation`|`100`|
|**user_id**|`string`|contextual|The user identifier. This should only be populated with a valid user id. This _**MUST NOT**_ be populated with any other string (e.x. "undefined", "null"). Using an undefined object is permitted.|`1234567890`|`100`|
|**user_login_state**|`string`|required|Set on all events with the authentication status of the visitor.|`authenticated`, `anonymous`|`100`|
|**user_type**|`string`|contextual|Set on all events with the authentication type of the visitor are they new or returning|`new`, `returning`|`100`|
|**event_form_custkey**|`string`|contextual|This is the ID created by Salesforce Marketing cloud|`12345...`|`100`|
|**event_form_hashemail**|`string`|contextual|Converts the submitted email into hased format|`b642b4217b34b1e8d3bd915fc65c4452 (MD5)`|`100`|
