## List entries

Lists entries.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |
| entryId | path | string | GUID | The entry identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| pageIndex | query | number | integer | The index of the page |
| pageSize | query | number | integer | The number of results per page. The default is 25. |
| order | query | string |  | A comma-separated list of the field Ids to order the results by. Prefix field Id with - for descending order. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code. |
| dataFormat | query | string | | The data format of the entry, either *entries*, *assets* or *all*. The default is *entries*. |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/entries/
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [PagedList&lt;Entry&gt;](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
