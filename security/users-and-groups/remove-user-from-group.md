---
description: A user can be removed from a group by sending a DELETE request specifying the group and user identifiers.
---

# Remove user from a group

A user can be removed from a group by sending a DELETE request specifying the group and user identifiers.

<span class="label label--delete">DELETE</span> /api/management/security/groups/**{groupId}**/users/**{userId}**

| Name    | Parameter type | Type   | Format | Description           |
|:--------|:---------------|:-------|:-------|:----------------------|
| groupId | path           | string | GUID   | The group identifier. |
| userId  | path           | string | GUID   | The user identifier.  |

## Example request

```json
DELETE: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |