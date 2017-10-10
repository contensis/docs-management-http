## Create an entry

Creates a new entry resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |

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
| 201 | Created | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Project does not exist

A project must exist to be able to create entries. If you attempt to create an entry in a project which doesn't exist you will get the following response. 

```http
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the entry",
    "data": [
        {
            "field": "projectId",
            "message": "The project does not exist"
        }
    ],
    "type": "Validation"
}
```


#### Content type does not exist

The published content type must exist to be able to create an entry. If you attempt to create an entry for a content type which doesn't exist or hasn't been published you will get the following response.

```http
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the entry",
    "data": [
        {
            "field": "contentType",
            "message": "The content type 'movie' does not exist"
        }
    ],
    "type": "Validation"
}
```