---
description: Gets the workflow definitions for a project.
---
## List workflow definitions

Gets the workflow definitions for a project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/workflow/definitions/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| pageIndex | query | number | integer | The index of the page |
| pageSize | query | number | integer | The number of results per page. The default is 25. |

### Example request

```http
GET: /api/management/projects/movieDb/workflow/definitions?versionStatus=published
```

### Response message

| HTTP status code | Reason              | Response model                               |
|:-----------------|:--------------------|:---------------------------------------------|
| 200              | Success             | [PagedList&lt;Workflow Definition&gt;](/model/workflow-definition.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)             |
| 404              | NotFound            | [Error](/key-concepts/errors.md)             |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)             |

