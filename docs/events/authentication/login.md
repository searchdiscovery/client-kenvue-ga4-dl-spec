# Login

Fire whenever a user logs in to an account.

## Javascript Code

```js
// When:
// User logs into an account

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null, user_data: null });  // Clear the previous event_data and user_data objects.
dataLayer.push({
  event: "login",
  event_data: {
    method: "<method>", // REQUIRED | string | ex. google, linkedin, email and password
  },
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
|method|string|required|The method used to login.|`google`, `linkedin`, `email and password`|`100`|
|user_id|string|contextual|The user identifier. This should only be populated with a valid user id. This _**MUST NOT**_ be populated with any other string (e.x. "undefined", "null"). Using an undefined object is permitted.|`1234567890`|`100`|
|user_login_state|string|required|Set on all events with the authentication status of the visitor.|`authenticated`, `anonymous`|`100`|
|user_type|string|contextual|Set on all events with the authentication type of the visitor are they new or returning|`new`, `returning`|`100`|
