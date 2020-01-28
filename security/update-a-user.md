---
description: Updating a user can be done by PUT'ing an updated version of the user resource. 
---

## Create a user

Updates an existing user resource.

<span class="label label--put">PUT</span> /api/management/security/users/**{userId}**

### Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                             |
|:----------|:---------------|:-------|:-------|:--------------------------------------------------------------------------------------------------------|
| userId    | path           | string | GUID   | The user identifier.                                                                                    |

### Example request

```json
PUT: /api/management/security/users/4b262379-5bbe-421e-a429-f6e2ab5a849b
{
        "id": "4b262379-5bbe-421e-a429-f6e2ab5a849b",
        "username": "t.durden",
        "email": "s.yearsley@zengenti.com",
        "title": "Mr",
        "firstname": "Tyler",
        "surname": "Durden",
        "properties": {
            "favouriteGenre": "drama"
        }
    },
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |