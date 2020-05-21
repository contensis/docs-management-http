## Get content types for entry usage

Gets a list of content types which have entries linking to the current entry

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/usage/contentTypes

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| entryId | path | string | GUID | The entry identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code. |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c/usage/contentTypes
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [List&lt;EntryUsageContentTypeInfo&gt;](/model/entry-usage-content-type-info.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
