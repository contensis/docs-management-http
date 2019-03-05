---
description: Get nodes that have a specified entry assigned.
---
## Get nodes by entry id

Gets all nodes that have a specified entry assigned.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes?entryId=**{entry-id}**

### Example request

```http
GET: /api/management/projects/website/nodes?entryId=d6bdea41-729c-4a07-85bf-a392aa0afc2b
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Node](/model/node.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
