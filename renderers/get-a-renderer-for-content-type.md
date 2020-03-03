---
description: Gets a renderer resource with the specified content type assigned.
---
## Get a renderer

Gets a renderer resource by it's identifier.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/renderers/?contentTypeId=**{contentTypeId}**

## Parameters

| Name          | Parameter type | Type   | Format | Description                                                                                            |
|---------------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId     | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| contentTypeId | query          | string |        | The content type identifier to match a renderer                                                        |

### Remarks

### Example request

```HTTP
GET: /api/management/projects/website/renderers/?contentTypeId=event
```

### Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | OK                  | [Renderer](/model/renderer.md)   |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

