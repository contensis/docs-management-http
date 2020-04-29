---
description: Gets the users as direct members of the group
---

## Get group user membership by group id

Gets the users as direct members of the group

<span class="label label--get">GET</span> /api/management/security/groups/**{groupId}**/users

### Parameters

| Name    | Parameter type | Type   | Format | Description          |
|:--------|:---------------|:-------|:-------|:---------------------|
| groupId | path           | string | GUID   | The group identifier |

### Example request

```http
GET: /api/management/security/groups/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c/users
```

### Response message

| HTTP status code | Reason              | Response model                          |
|:-----------------|:--------------------|:----------------------------------------|
| 200              | Success             | [PagedList&lt;User&gt;](/model/user.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)        |
| 404              | NotFound            | [Error](/key-concepts/errors.md)        |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)        |

---

## Get group user membership by group name

Gets the users as direct members of the group

<span class="label label--get">GET</span> /api/management/security/groups/**{groupName}**/users

### Parameters

| Name      | Parameter type | Type   | Format | Description    |
|:----------|:---------------|:-------|:-------|:---------------|
| groupName | path           | string |        | The group name |

### Example request

```http
GET: /api/management/security/groups/Paper%20Street%20Soap%20Company/users
```

### Response message

| HTTP status code | Reason              | Response model                          |
|:-----------------|:--------------------|:----------------------------------------|
| 200              | Success             | [PagedList&lt;User&gt;](/model/user.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)        |
| 404              | NotFound            | [Error](/key-concepts/errors.md)        |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)        |