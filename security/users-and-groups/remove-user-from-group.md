---
description: A user can be removed from a group by sending a DELETE request specifying the group and user identifiers.
---

# Remove user from a group

A user can be removed from a group by sending a DELETE request specifying the group and user identifiers.

<span class="label label--delete">DELETE</span> /api/management/security/groups/**{groupIdentifier}**/users/**{userIdentifier}**

| Name            | Parameter type | Type   | Format   | Description                       |
| :-------------- | :------------- | :----- | :------- | :-------------------------------- |
| groupIdentifier | path           | string | GUID     | The group id as the identifier.   |
| groupIdentifier | path           |        | Name     | The group name as the identifier. |
| userIdentifier  | path           | string | GUID     | The user id as the identifier.    |
| userIdentifier  | path           |        | Username | The username as the identifier.   |
| userIdentifier  | path           |        | Email    | The user email as the identifier. |

## Example requests

```http
DELETE: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
DELETE: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
DELETE: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/tdurden
```

```http
DELETE: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/users/t.durden@fightclub.com
```

```http
DELETE: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/t.durden@fightclub.com
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 409              | Conflict            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
