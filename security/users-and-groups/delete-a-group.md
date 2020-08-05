---
description: Deleting a group can be done by sending a DELETE request to the group resource location
---

# Delete a group

Deleting a group can be done by sending a DELETE request to the group resource location.

<span class="label label--delete">DELETE</span> /api/management/security/groups/**{groupIdentifier}**

### Parameters

| Name            | Parameter type | Type   | Format | Description                       |
| :-------------- | :------------- | :----- | :----- | :-------------------------------- |
| groupIdentifier | path           | string | GUID   | The group id as the identifier.   |
| groupIdentifier | path           |        | Name   | The group name as the identifier. |

## Example requests

```http
DELETE: /api/management/security/groups/cd7b3be9-c45a-4a35-b359-f978f9dbeb9a
```

```http
DELETE: /api/management/security/groups/Paper%20Street%20Soap%20Company
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
