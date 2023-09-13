# Sign Up Start

Fire whenever a user views the first step of the account creation form.

## Javascript Code

```js
// When:
// User views the first step of account creation process

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'sign_up_start'
  event_data: {
    method: "<method>", // REQUIRED | string | ex. google, linkedin, email and password
  },
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|method|string|required|The method by which a user created a new account.|`local`, `social_login`|`100`|
