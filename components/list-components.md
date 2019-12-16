---
description: Gets the components for a project.
---
## List components

Gets the components for a project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/components/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |

### Example request

```http
GET: /api/management/projects/movieDb/components?versionStatus=published
```

### Response message

| HTTP status code | Reason              | Response model                               |
|:-----------------|:--------------------|:---------------------------------------------|
| 200              | Success             | [Content Type [...]](/model/content-type.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)             |
| 404              | NotFound            | [Error](/key-concepts/errors.md)             |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)             |

