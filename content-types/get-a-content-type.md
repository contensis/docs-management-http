---
description: Gets an existing content type by the content type Id.
---
# Content types

## Get a content type

Gets an existing content type by the content type Id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| contentTypeId | path | string |  | The content type identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| version | query | string | {Major}.{Minor} | The version number of the resource. |

### Example request

```http
GET: /api/management/projects/movieDb/contenttypes/movie/
```

### Response message

| HTTP status code | Reason              | Response model                         |
|:-----------------|:--------------------|:---------------------------------------|
| 200              | Success             | [Content Type](/model/content-type.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 404              | NotFound            | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |

### Remarks

If a specific *versionNo* value has been provided then the *versionStatus* value will be ignored.