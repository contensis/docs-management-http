## Get entry usage

Gets a list of entries which link to the current entry

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/usage

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| entryId | path | string | GUID | The entry identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| pageIndex | query | number | integer | The index of the page |
| pageSize | query | number | integer | The number of results per page. The default is 25. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code. |
| contentTypeId | query | string |  | The content type identifier. Filters the results to the specified content type only. If this is not specified then entries for all content types will be returned. |
| q | query | string |  | Filters the results to entries which contain the specified string in either the entry title or the entry description. |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c/usage
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [PagedList&lt;EntryUsageInfo&gt;](/model/entry-usage-info.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
