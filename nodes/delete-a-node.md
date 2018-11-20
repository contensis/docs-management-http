---
description: Deletes a node.
---
## Delete a node

Deletes a node by Id.

<span class="label label--get">DELETE</span> /api/management/projects/{projectId}/nodes/{nodeId}/

### Example request

```json
DELETE: /api/management/projects/website/nodes/d6bdea41-729c-4a07-85bf-a392aa0afc2b
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 204 | NoContent | [Node](/model/node.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |