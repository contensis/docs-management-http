---
description: A child group can be added to a group by sending a PUT request specifying the group identifiers.
---

# Add child group to a group

A child group can be added to a group by sending a PUT request specifying the group identifiers.

<span class="label label--put">PUT</span> /api/management/security/groups/**{groupId}**/childGroups/**{childGroupId}**

| Name         | Parameter type | Type   | Format | Description           |
|:-------------|:---------------|:-------|:-------|:----------------------|
| groupId      | path           | string | GUID   | The group identifier. |
| childGroupId | path           | string | GUID   | The child group identifier.  |

## Example request

```json
PUT: /api/management/security/groups/6254736c-70e1-43b0-b769-f8e0f6359862/childGroups/3d063773-2ca9-4baf-90e1-ed674fa68640
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

