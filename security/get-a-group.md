---
description: A group resource can be retrieved by it's GUID identifier
---

## Get a group by id

A group="label label--get">GET</span> /api/management/security/groups/**{groupId}**

### Parameters

| Name    | Parameter type | Type   | Format | Description           |
|:--------|:---------------|:-------|:-------|:----------------------|
| groupId | path           | string | GUID   | The group identifier. |

### Example request

```http
GET: /api/management/security/groups/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Group](/model/group.md)          |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

---

## Get a group by name

A group="label label--get">GET</span> /api/management/security/groups/**{groupName}**

### Parameters

| Name      | Parameter type | Type   | Format | Description     |
|:----------|:---------------|:-------|:-------|:----------------|
| groupName | path           | string |        | The group name. |

### Example request

```http
GET: /api/management/security/groups/Paper%20Street%20Soap%20Company
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Group](/model/group.md)          |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |