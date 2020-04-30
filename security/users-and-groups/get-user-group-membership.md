---
description: Gets the users as direct members of the group
---

## Get group membership for a user

Gets the groups the user is a member of.

<span class="label label--get">GET</span> /api/management/security/users/**{userId}**/groups

### Parameters

| Name              | Parameter type | Type   | Format | Description                                                           |
|:------------------|:---------------|:-------|:-------|:----------------------------------------------------------------------|
| userId            | path           | string | GUID   | The user identifier                                                   |
| includeInherited | query          | bool   |        | If set to true, the response will include all inherited parent groups |

### Example request

```http
GET: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c/groups?includeInherited=true
```

### Response message

| HTTP status code | Reason              | Response model                            |
|:-----------------|:--------------------|:------------------------------------------|
| 200              | Success             | [PagedList&lt;Group&gt;](/model/group.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |

