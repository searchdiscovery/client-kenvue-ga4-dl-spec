---
title: Survey Error
---

# Survey Error

Fire whenever a user unsuccessfully completes a survey. 

This is in contrast to [`complete_survey`](../../events/survey/complete_survey.md) which occurs when a submission succeeds.

## Javascript Code

```js
// When:
// User unsuccessfully completes a survey and survey input is not successfully received and processed. Contrasts survey_complete in which a submission is received and processed successfully. 

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'survey_error',
  event_data: {
    error_message: '<error_message>', // REQUIRED | string | ex. Phone number should follow the format (xxx) xxx-xxxx, Must be a valid email address
    identifier: '<identifier>', // REQUIRED | string | ex. cancel_subscription_flow, free_trial
    name: '<name>', // REQUIRED | string | ex. cancel_subscription_flow, free_trial
    type: '<type>', // REQUIRED | string | ex. survey, lead_generation
    step_name: '<step_name>', // contextual | string | ex. survey_field_validation, server_error
    step_number: '<step_number>' // contextual | integer | ex. 1, 2, 3, 4, 5

  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**error_message**|`string`|required|The specific error that occurred. If an error message is shown to the user, this should be populated with that text.|`Phone number should follow the format (xxx) xxx-xxxx, Must be a valid email address`|`100`|
|**identifier**|`string`|required|The survey machine-readable name. This should be a unique value specific to this survey, if one exists. If one does not exist, this can also be populated with the same value as the `name`.|`cancel_subscription_flow`, `free_trial`|`100`|
|**name**|`string`|required|The survey human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the survey with. It should be lowercase snake_case.|`cancel_subscription_flow`, `free_trial`|`100`|
|**type**|`string`|required|The type of error that occurred.|`survey_field_validation`, `server_error`|
|**step_name**|`string`|contextual|The human-readable name of the current step of the survey.|`why_are_you_cancelling`,`which_product`|`100`|
|**step_number**|`integer`|contextual|The current step/section integer of the survey flow.|`1`,`2`,`3`,`4`,`5`|`100`|
