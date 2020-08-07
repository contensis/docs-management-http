---
description: A child group can be removed from a group by sending a DELETE request specifying the group identifiers.
---

# Remove child group from a group

A child group can be removed from a group by sending a DELETE request specifying the group identifiers.

<span class="label label--put">DELETE</span> /api/management/security/groups/**{groupIdentifier}**/childGroups/**{childGroupIdentifier}**

| Name                 | Parameter type | Type                                        | Description                  |
| :------------------- | :------------- | :------------------------------------------ | :--------------------------- |
| groupIdentifier      | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |
| childGroupIdentifier | path           | [GroupIdentifier](/security/identifiers.md) | One of the group identifiers |

## Example requests

```http
DELETE: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/childGroups/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
DELETE: /api/management/security/groups/Paper%20Street%20Soap%20Company/childGroups/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
DELETE: /api/management/security/groups/Paper%20Street%20Soap%20Company/childGroups/Liposuction%20Technicians
```

```http
DELETE: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/childGroups/Liposuction%20Technicians
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
