---
description: Creates a new renderer resource.
---
## Create a renderer

Creates a new renderer resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/renderers

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

### Remarks

### Example request

```json
POST: /api/management/projects/website/renderers

{
    "id": "newsRecord",
    "name": "News record",
    "description": "Renders news record entries with rules for country (Populo)",
    "assignedContentTypes": [
        "newsRecord"
    ],
    "rules": [
        {
            "return": {
                "blockId": "news",
                "endpointId": "news-record"
            }
        }
    ]
}
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 202              | No Content            |                                  |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | NotFound              | [Error](/key-concepts/errors.md) |
| 409              | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422              | ValidationError       | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |




