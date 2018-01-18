---
description: Publishes an entry.
---
## Publish an entry

Publishes an entry.

<span class="label label--get">PUT</span> /api/management/workflow

### Parameters

None.

### Example request

```json
PUT: /api/management/workflow

{  
   "projectId":"movieDb",
   "objectId":"71f73a9b-2a13-4d63-bcc1-e8ee5047b01c",
   "language":"en-GB",
   "type":"Entry",
   "objectVersion":"0.4",
   "workflowName":"ContensisDefault",
   "events":["submit","approve"]
}

```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | BadRequest | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
