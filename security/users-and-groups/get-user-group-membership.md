---
description: Gets the users as direct members of the group
---

## Get group membership for a user

Gets the groups the user is a member of.

<span class="label label--get">GET</span> /api/management/security/users/**{userIdentifier}**/groups

### Parameters

| Name             | Parameter type | Type   | Format   | Description                                                           |
| :--------------- | :------------- | :----- | :------- | :-------------------------------------------------------------------- |
| userIdentifier   | path           | string | GUID     | The user id as the identifier.                                        |
| userIdentifier   | path           |        | Username | The username as the identifier.                                       |
| userIdentifier   | path           |        | Email    | The user email as the identifier.                                     |
| includeInherited | query          | bool   |          | If set to true, the response will include all inherited parent groups |

### Example requests

```http
GET: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c/groups?includeInherited=true
```

```http
GET: /api/management/security/users/tdurden/groups?includeInherited=true
```

```http
GET: /api/management/security/users/t.durden@fightclub.com/groups?includeInherited=true
```

### Response message

| HTTP status code | Reason              | Response model                            |
| :--------------- | :------------------ | :---------------------------------------- |
| 200              | Success             | [PagedList&lt;Group&gt;](/model/group.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |
