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

Only the current user and a member of the System Administrators group can update a user resource

## Example request

```json
PUT: /api/management/security/users/4b262379-5bbe-421e-a429-f6e2ab5a849b
{
    "username": "tdurden",
    "email": "t.turden@fightclub.com",
    "title": "Mr",
    "firstname": "Tyler",
    "lastname": "Durden",
    "timezone": "America/New_York",
    "language": "en-US",
    "avatar": "/api/management/security/users/56a7c76c-2e80-403d-a960-fd93e7523d06/avatar?w=600&h=800",
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