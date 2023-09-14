# Sign Up

Fire whenever a user successfully creates an account.

## Javascript Code

```js
// When:
// User successfully creates an account

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'sign_up',
  event_data: {
    method: "<method>", // REQUIRED | string | ex. google, linkedin, email and password
  },
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|method|string|required|The method by which a user created a new account.|`local`, `social_login`|`100`|

