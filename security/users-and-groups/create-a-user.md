---
description: Creating a user can be done by POST'ing user profile details resource to the users resource collection. 
---

# Create a user

Creating a user can be done by POST'ing user profile details resource to the users resource collection. 

<span class="label label--post">POST</span> /api/management/security/users/

## Example request

```json
POST: /api/management/security/users/
{
    "username": "tdurden",
    "email": "t.turden@fightclub.com",
    "firstname": "Tyler",
    "lastname": "Durden",
    "timezone": "America/New_York",
    "language": "en-US",
    "custom": {
        "department": "Soap sales"
    },
    "credentials": {
        "password": "pr0j3ctM4yh3m"
    }
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 201              | Created             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 409              | Conflict            | [Error](/key-concepts/errors.md) |
| 422              | UnprocessableEntity | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |