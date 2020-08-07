---
description: Updating a user can be done by PUT'ing an updated version of the user profile resource.
---

# Update a user

Updating a user can be done by PUT'ing an updated version of the user profile resource.

<span class="label label--put">PUT</span> /api/management/security/users/**{userIdentifier}**

## Parameters

| Name           | Parameter type | Type                                       | Description                 |
| :------------- | :------------- | :----------------------------------------- | :-------------------------- |
| userIdentifier | path           | [UserIdentifier](/security/identifiers.md) | One of the user identifiers |

## Remarks

Only the current user and a member of the System Administrators group can update a user resource

## Example request

```http
PUT: /api/management/security/users/4b262379-5bbe-421e-a429-f6e2ab5a849b
{
    "username": "tdurden",
    "email": "t.turden@fightclub.com",
    "firstname": "Tyler",
    "lastname": "Durden",
    "timezone": "America/New_York",
    "language": "en-US",
    "custom": {
        "department": "Soap sales"
    }
}
```

```http
PUT: /api/management/security/users/tdurden
{
    "username": "tdurden",
    "email": "t.turden@fightclub.com",
    "firstname": "Tyler",
    "lastname": "Durden",
    "timezone": "America/New_York",
    "language": "en-US",
    "custom": {
        "department": "Soap sales"
    }
}
```

```http
PUT: /api/management/security/users/t.durden@fightclub.com
{
    "username": "tdurden",
    "email": "t.turden@fightclub.com",
    "firstname": "Tyler",
    "lastname": "Durden",
    "timezone": "America/New_York",
    "language": "en-US",
    "custom": {
        "department": "Soap sales"
    }
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
