---
description: Lists entries by content type.
---
# List entries by content type

Lists entries by content type.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/entries

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| entryId | path | string | GUID | The entry identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| pageIndex | query | number | integer | The index of page. |
| pageSize | query | number | integer | The number of results per page. The default is 25. |
| order | query | string |  | A comma-separated list of the field Ids to order the results by. Prefix field Id with - for descending order. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code. |

### Example request

```http
GET: /api/management/projects/movieDb/contenttypes/movie/entries/
```

### Response message

| HTTP status code | Reason              | Response model                            |
|:-----------------|:--------------------|:------------------------------------------|
| 200              | Success             | [PagedList&lt;Entry&gt;](/model/entry.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |
