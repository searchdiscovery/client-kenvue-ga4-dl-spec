# Detect User

This is a conditional event that should only be fired in very specific cases. It is intended to cover cases where a user authentication system exists on the site but the user authentication state may not be known by the time the page_view event is sent. In that case, send this event as soon as the user authentication state is known.

_**Do not**_ clear the page_data variable before setting user_login_state here as this is not a page view.

If the "user_id" is _**NOT**_ available, _**DO NOT**_ populate with an empty string (ex. "") or undefined as a string (ex. "undefined"). This value must _**ONLY**_ be populated with a valid user id. If this value is not available, then either _**DO NOT**_ include the parameter in the data layer push or populate with an undefined object (not a string)

## Javascript Code

```js
// When:
// User authentication exists, but the 'authentication state' may not be known by the time the page_view event is fired.
// NOTE: Do not clear the page_data variable before setting user_login_state here. This is not a page view.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null, user_data: null });  // Clear the previous event_data and user_data objects.
dataLayer.push({
  event: "detect_user",
  page_data: {
    user_login_state: '<user_login_state>', // REQUIRED | string | ex. authenticated, anonymous
  },
  user_data: {
    user_id: "<user_id>", // contextual | string | ex. 1234567890
    user_type: '<user_type>' // contextual | string | ex. new, returning
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|user_id|string|contextual|The user identifier. This should only be populated with a valid user id. This _**MUST NOT**_ be populated with any other string (e.x. "undefined", "null"). Using an undefined object is permitted.|`1234567890`|`100`|
|user_login_state|string|required|Set on all events with the authentication status of the visitor.|`authenticated`, `anonymous`|`100`|
|user_type|string|contextual|Set on all events with the authentication type of the visitor are they new or returning|`new`, `returning`|`100`|
