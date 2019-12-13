---
description: Gets the content types for a project.
---
## List content types

Gets the content types for a project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| dataFormat | query | string |  | The specific dataFormat, e.g. *entry*, *asset*. The default is all. |

### Example request

```http
GET: /api/management/projects/movieDb/contenttypes?versionStatus=published&dataFormat=entry
```

### Response message

| HTTP status code | Reason              | Response model                               |
|:-----------------|:--------------------|:---------------------------------------------|
| 200              | Success             | [Content Type [...]](/model/content-type.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)             |
| 404              | NotFound            | [Error](/key-concepts/errors.md)             |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)             |

