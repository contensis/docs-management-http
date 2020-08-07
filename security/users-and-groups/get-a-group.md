---
description: A group resource can be retrieved by it's GUID identifier
---

# Get a group by id

A group resource can be retrieved any valid [GroupIdentifier](/security/identifiers.md).

<span class="label label--get">GET</span> /api/management/security/groups/**{groupIdentifier}**

## Parameters

| Name            | Parameter type | Type                                        | Description                  |
| :-------------- | :------------- | :------------------------------------------ | :--------------------------- |
| groupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |

## Example requests

```http
GET: /api/management/security/groups/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

```http
GET: /api/management/security/groups/Paper%20Street%20Soap%20Company
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 200              | Success             | [Group](/model/group.md)         |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
