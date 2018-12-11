---
description: An entry definition in the Management API contains a mixture of standard properties and properties that have been defined by the content type that an entry is based on.
---
# Entries

An entry definition in the Management API contains a mixture of standard properties and properties that have been defined by the content type that an [entry] (https://zenhub.zengenti.com/Contensis/11.3/kb/content-types-and-entries/entries/entries-overview.aspx) is based on.

## Get an entry

Gets an existing entry by its id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/**{entryId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| entryId | path | string | GUID | The entry identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| version | query | string | [versionNo](/model/version.md#versionNo)  | The specific version requested. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code. |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/entries/movie/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Remarks

If a specific *versionNo* value has been provided then the *versionStatus* value will be ignored.
