---
description: Creating a group can be done by POST'ing user details resource to the group resource collection. 
---

# Create a group

Updating a group can be done by PUT'ing group details resource to the group resource location. 

<span class="label label--put">PUT</span> /api/management/security/groups/**{groupId}**

### Parameters

| Name    | Parameter type | Type   | Format | Description           |
|:--------|:---------------|:-------|:-------|:----------------------|
| groupId | path           | string | GUID   | The group identifier. |

## Example request

```json
POST: /api/management/security/groups/cd7b3be9-c45a-4a35-b359-f978f9dbeb9a
{
    "name": "Paper Street Soap Company",
    "Description": "Employees of the Paper Street Soap Company", 
    "type": "contensis",
    "custom" : {
        "clientId": "PSSC"
    },
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | OK                  | [Group](/model/group.md)         |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | UnprocessableEntity | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |