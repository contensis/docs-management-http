---
description: Updates an existing renderer resource.
---
## Update a renderer

Updates an existing renderer resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/renderers/**{rendererId}**

## Parameters

| Name       | Parameter type | Type   | Format | Description                                                                                            |
|------------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId  | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| rendererId | path           | string |        | The renderer identifier                                                                                |

### Remarks

### Example request

```json
PUT: /api/management/projects/website/renderers/newsRecord

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
    ],
    "version"
}
```

### Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | OK                  | [Renderer](/model/renderer.md)   |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

