---
description: Creates a new node.
---
## Create a node

Creates a new node.

<span class="label label--post">POST</span> /api/management/projects/{projectId}/nodes/{parentNodeId}/children

### Example request

```json
POST: /api/management/projects/website/nodes/f3322e4f-72b5-4064-be88-fcfed6c82635/children


{
	"id": "d6bdea41-729c-4a07-85bf-a392aa0afc2b",
	"parentId": "f3322e4f-72b5-4064-be88-fcfed6c82635",
	"projectId": "website",
	"name": {
		"en-GB": "tiger-escaped-from-zoo",
		"fr-FR": "tigre-s-est-echappe-du-zoo"
	},
    "availableLanguages": [
        "en-GB",
        "fr-FR"
    ],
	"entryId": "9272ac06-1b3a-4e68-ac1b-a05828b0f7d6",
	"hasChildren": false
}
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | [Node](/model/node.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Parent id

A node must have a parent id. If you attempt to create a node without a parent id you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "The parent id cannot be an empty guid"
        }
    ],
    "type": "Validation"
}
