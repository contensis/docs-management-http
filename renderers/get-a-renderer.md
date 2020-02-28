---
description: Gets a renderer resource by it's identifier.
---
## Get a renderer

Gets a renderer resource by it's identifier.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/renderers/**{rendererId}**

## Parameters

| Name       | Parameter type | Type   | Format | Description                                                                                            |
|------------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId  | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| rendererId | path           | string |        | The renderer identifier                                                                                |

### Remarks

### Example request

```HTTP
GET: /api/management/projects/website/renderers/newsRecord
```

### Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | OK                  | [Renderer](/model/renderer.md)   |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

