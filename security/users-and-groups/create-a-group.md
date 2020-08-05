---
description: Creating a group can be done by POST'ing user details resource to the group resource collection.
---

# Create a group

Creating a group can be done by POST'ing group details resource to the group resource collection.

<span class="label label--post">POST</span> /api/management/security/groups/

## Example request

```http
POST: /api/management/security/groups/
{
    "name": "Paper Street Soap Company",
    "Description": "Employees of the Paper Street Soap Company",
    "type": "contensis",
    "custom" : {
        "clientId": "PSSC"
    }
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 201              | Created             | [Group](/model/group.md)         |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 409              | Conflict            | [Error](/key-concepts/errors.md) |
| 422              | UnprocessableEntity | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
