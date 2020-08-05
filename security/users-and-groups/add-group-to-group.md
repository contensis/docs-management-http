---
description: A child group can be added to a group by sending a PUT request specifying the group identifiers.
---

# Add child group to a group

A child group can be added to a group by sending a PUT request specifying the group identifiers.

<span class="label label--put">PUT</span> /api/management/security/groups/**{groupIdentifier}**/childGroups/**{childGroupIdentifier}**

| Name                 | Parameter type | Type   | Format | Description                             |
| :------------------- | :------------- | :----- | :----- | :-------------------------------------- |
| groupIdentifier      | path           | string | GUID   | The group id as the identifier.         |
|                      |                |        | Name   | The group name as the identifier.       |
| childGroupIdentifier | path           | string | GUID   | The child group id as the identifier.   |
|                      |                |        | Name   | The child group name as the identifier. |

## Remarks

A group cannot be added as a child group of itself.

## Example requests

```http
PUT: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/childGroups/3d063773-2ca9-4baf-90e1-ed674fa68640
```

```http
PUT: /api/management/security/groups/Paper%20Street%20Soap%20Company/childGroups/Liposuction%20Technicians
```

```http
PUT: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/childGroups/Liposuction%20Technicians
```

```http
PUT: /api/management/security/groups/Paper%20Street%20Soap%20Company/childGroups/3d063773-2ca9-4baf-90e1-ed674fa68640
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
