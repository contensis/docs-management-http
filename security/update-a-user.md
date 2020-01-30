---
description: Updating a user can be done by PUT'ing an updated version of the user profile resource. 
---

# Update a user

Updating a user can be done by PUT'ing an updated version of the user profile resource. 

<span class="label label--put">PUT</span> /api/management/security/users/**{userId}**

## Parameters

| Name   | Parameter type | Type   | Format | Description          |
|:-------|:---------------|:-------|:-------|:---------------------|
| userId | path           | string | GUID   | The user identifier. |

## Remarks

TODO: Details around permissions

## Example request

```json
PUT: /api/management/security/users/4b262379-5bbe-421e-a429-f6e2ab5a849b
{
    "username": "tdurden",
    "email": "t.turden@fightclub.com",
    "title": "Mr",
    "firstname": "Tyler",
    "lastname": "Durden",
    "avatarUrl": "https://mywebsite/users/tyler.jpg",
    "timezone": "America/New_York",
    "language": "en-US",
    "custom": {
        "department": "Soap sales"
    }
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |