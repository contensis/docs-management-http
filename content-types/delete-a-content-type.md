---
description: Deletes a content type within a specific project.
---

## Delete a content type

Deletes a content type within a specific project.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**

### Example request

```http
DELETE: /api/management/projects/movieDb/contenttypes/actor
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

