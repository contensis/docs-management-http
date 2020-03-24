---
description: Gets a renderer resource by it's identifier.
---
## List renderers

Gets all renderers for a project as a paged list.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/renderers/

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

### Example request

```HTTP
GET: /api/management/projects/website/renderers/
```

### Response messages

| HTTP status code | Reason              | Response model                                 |
|:-----------------|:--------------------|:-----------------------------------------------|
| 200              | OK                  | PagedList&lt;[Renderer](/model/renderer.md)&gt; |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)               |
| 404              | NotFound            | [Error](/key-concepts/errors.md)               |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)               |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)               |

