---
description: Get root node.
---
## Get the root node

Gets the root node of the specified project. 

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/

### Example request

```http
GET: /api/management/projects/website/nodes/
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Node](/model/node.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
