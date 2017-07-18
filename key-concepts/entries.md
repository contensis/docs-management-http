# Entries

## Get an entry

Gets an existing entry by its id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/**{entryId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId | path | string | GUID | The entry identifier |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest* |
| version | query | string | [versionNo](/model/version.md#versionNo)  | The specific version requested |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code |

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






## Create an entry

Creates a new entry resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |

### Example request

```http
POST: /api/management/projects/movieDb/entries/

{
    "title": "Back to the future",
    "tagline": "He's the only kid ever to get into trouble before he was born.",
    "overview": "Marty McFly, a typical American teenager of the Eighties, is accidentally sent back to 1955 in a plutonium-powered DeLorean \"time machine\" invented by slightly mad scientist. During his often hysterical, always amazing trip back in time, Marty must make certain his teenage parents-to-be meet and fall in love - so he can get back to the future.",
    "trailer": "https://www.youtube.com/watch?v=qvsgGtivCgs",
    "releaseDate": "1985-07-02T23:00:00Z",
    "actors": [
        {
            "sys": {
                "id": "a1c983d6-4aaf-4456-9f3d-a6eac3139f1c",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        },
        {
            "sys": {
                "id": "16f6f2de-e901-4bda-bf3f-092b93ae62a9",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        },
        {
            "sys": {
                "id": "09b87c0b-67b2-4028-9358-e29ff16f11da",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        }
    ],
    
    "sys": {
        "contentTypeId": "movie",
        "projectId": "movieDb",
        "language": "en-GB",
        "dataFormat": "entry",
    }
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | [Content Type](/model/content-type.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
**TODO: Add validation responses**

### Validations

| Type | Description |
|-|-|
| Project does not exist | A project must exist to be able to create content types |
| Content type does not exist | The published content type must exist to be able to create an entry |






## Update an entry

Updates an entry resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/entries/**{entryId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId   | path | string |  | The entry identifier |

### Example request

```http
PUT: /api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c

{
    "title": "Back to the future",
    "tagline": "He's the only kid ever to get into trouble before he was born.",
    "overview": "Marty McFly, a typical American teenager of the Eighties, is accidentally sent back to 1955 in a plutonium-powered DeLorean \"time machine\" invented by slightly mad scientist. During his often hysterical, always amazing trip back in time, Marty must make certain his teenage parents-to-be meet and fall in love - so he can get back to the future.",
    "trailer": "https://www.youtube.com/watch?v=qvsgGtivCgs",
    "releaseDate": "1985-07-02T23:00:00Z",
    "actors": [
        {
            "sys": {
                "id": "a1c983d6-4aaf-4456-9f3d-a6eac3139f1c",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        },
        {
            "sys": {
                "id": "16f6f2de-e901-4bda-bf3f-092b93ae62a9",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        },
        {
            "sys": {
                "id": "09b87c0b-67b2-4028-9358-e29ff16f11da",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        }
    ],
    
    "sys": {
        "id": "71f73a9b-2a13-4d63-bcc1-e8ee5047b01c",
        "contentTypeId": "movie",
        "projectId": "movieDb",
        "language": "en-GB",
        "dataFormat": "entry",
        "version": {
            "versionNo": "1.0"
        }
    }
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Content Type](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
**TODO: Add validation responses**

### Validations

| Type | Description |
|-|-|
| Project does not exist | A project must exist to be able to create content types |
| Content type does not exist | The published content type must exist to be able to create an entry |


TODO: Explain the optimistic concurrency versioning model






## Publish an entry

Publishes an entry.

<span class="label label--get">PUT</span> /api/management/workflow

## Parameters

None.

### Example request

```http
PUT: /api/management/workflow

{  
   "projectId":"movieDb",
   "objectId":"71f73a9b-2a13-4d63-bcc1-e8ee5047b01c",
   "language":"en-GB",
   "type":"Entry",
   "objectVersion":"0.4",
   "workflowName":"ContensisDefault",
   "events":["submit","approve"]
}

```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Content Type [...]](/model/content-type.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | BadRequest | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |






## List content types

Gets the content types for a project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest* |
| dataFormat | query | string |  | The specific dataFormat, e.g. *entry*, *asset*. The default is all |

### Example request

```http
GET: /api/management/projects/movieDb/contenttypes?versionStatus=published&dataFormat=entry
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Content Type [...]](/model/content-type.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |






## List entries

Lists entries

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId | path | string | GUID | The entry identifier |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest* |
| pageIndex | query | number | integer | The index of the page |
| pageSize | query | number | integer | The number of results per page. The default is 25 |
| order | query | string |  | A comma-separated list of the field Ids to order the results by. Prefix field Id with - for descending order. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code |
| dataFormat | query | string | | The data format of the entry, either *entries*, *assets* or *all*. The default is *entries* |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/entries/
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |






## List entries by content type

Lists entries by content type

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/entries

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId | path | string | GUID | The entry identifier |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest* |
| pageIndex | query | number | integer | The index of page |
| pageSize | query | number | integer | The number of results per page. The default is 25 |
| order | query | string |  | A comma-separated list of the field Ids to order the results by. Prefix field Id with - for descending order. |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The variation language code |

### Example request

```http
GET: /api/management/projects/movieDb/contenttypes/movie/entries/
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |






## Delete an entry

Deletes an entry by its id.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId | path | string | GUID | The entry identifier |

### Example request

```http
Accept: application/json
DELETE: /api/management/projects/movieDb/entries/movie/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |





## Delete an entry variation

Deletes an entry variation by its id.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/**{language}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId | path | string | GUID | The entry identifier |
| language | path | string | [LanguageCode](/key-concepts/localization.md) | The variation language code |

### Example request

```http
DELETE: /api/management/projects/movieDb/entries/movie/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c/fr-FR
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | CannotDeleteDefaultVariation | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |