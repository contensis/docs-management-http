---
description: Updates an entry resource.
---
## Update an entry

Updates an entry resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/entries/**{entryId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console.|
| entryId   | path | string |  | The entry identifier. |

### Example request

```json
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

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Entry](/model/entry.md)         |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |


### Versioning

Contensis uses an optimistic concurrency versioning model. Rather than checking out entries and locking them we allow concurrent updating of entries. At the point in which you update an entry the version you pass in is checked to make sure it is the latest and no one else has created a newer version. If the version you pass in is the latest version then the entry will get updated. If you pass in a version which isn't now the latest then you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors updating the entry",
    "data": [
        {
            "field": "Entry.Variations.Values[0].entryVariation",
            "message": "The entry variation is not the latest"
        }
    ],
    "type": "Validation"
}
```
