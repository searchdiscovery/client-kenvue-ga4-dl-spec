# Logout

Fire whenever a user logs out of an account.

## Javascript Code

```js
// When:
// User logs out of an account

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ user_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "logout",
  page_data: {
    user_login_state: '<user_login_state>', // REQUIRED | string | ex. authenticated, anonymous
  },
  user_data: {
    user_id: "<user_id>", // contextual | string | ex. 1234567890
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|user_id|string|contextual|The user identifier. This should only be populated with a valid user id. This _**MUST NOT**_ be populated with any other string (e.x. "undefined", "null"). Using an undefined object is permitted.|`1234567890`|`100`|
|user_login_state|string|required|Set on all events with the authentication status of the visitor.|`authenticated`, `anonymous`|`100`|
