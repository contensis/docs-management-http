---
description: Gets the groups as direct child members of the group
---

# Get child group membership by group id

Gets the direct child group members of the group

<span class="label label--get">GET</span> /api/management/security/groups/**{groupIdentifier}**/groups

## Parameters

| Name            | Parameter type | Type                                        | Description                  |
| :-------------- | :------------- | :------------------------------------------ | :--------------------------- |
| groupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |

## Example requests

```http
GET: /api/management/security/groups/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c/groups
```

```http
GET: /api/management/security/groups/Paper%20Street%20Soap%20Company/groups
```

## Response message

| HTTP status code | Reason              | Response model                           |
| :--------------- | :------------------ | :--------------------------------------- |
| 200              | Success             | [PagedList&lt;Group&gt;](/model/list.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)         |
| 404              | NotFound            | [Error](/key-concepts/errors.md)         |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)         |
