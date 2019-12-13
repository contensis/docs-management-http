---
description: Creates a new content type resource.
---

# Update a content type

Updates a content type resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| contentTypeId | path | string |  | The content type identifier. |

## Example request

```json
PUT: /api/management/projects/movieDb/contenttypes/movie

{
    "id": "movie",
    "projectId": "movieDb",
    "name": {
        "en-GB": "Movie"
    },
    "description": {
        "en-GB": "A movie type"
    },
    "entryTitleField": "title",
    "entryDescriptionField": "overview",
    "fields": [
        {
            "id": "title",
            "name": {
                "en-GB": "Title"
            },
            "dataType": "string",
            "editor": {
                "id": "text",
                "instructions": {
                    "en-GB": "The title of the movie"
                },
                "properties": {
                    "placeholderText": {
                        "en-GB": "Enter the full title of the movie appropriate to the region"
                    }
                }
            }
        },
        {
            "id": "tagline",
            "name": {
                "en-GB": "Tagline"
            },
            "dataType": "string"
        },
        {
            "id": "overview",
            "name": {
                "en-GB": "Overview"
            },
            "dataType": "string",
            "dataFormat": "html",
        },
        {
            "id": "releaseDate",
            "name": {
                "en-GB": "Release Date"
            },
            "dataType": "dateTime",
            "validations": null
        },
        {
            "id": "actors",
            "name": {
                "en-GB": "Actors"
            },
            "dataType": "objectArray",
            "dataFormat": "entry",
            "validations": {
                "contentType": {
                    "contentType": "actor"
                }
            }
        }
    ],
    "defaultLanguage": "en-GB",
    "supportedLanguages": [
        "en-GB",
        "fr-FR",
        "de-DE",
        "es"
    ],
    "workflowId": "ContensisMultilingual",
    "dataFormat": "entry",
    "version": {
        "versionNo": "2.0"
    }
}
```

## Response message

| HTTP status code | Reason              | Response model                         |
|:-----------------|:--------------------|:---------------------------------------|
| 200              | Updated             | [Content Type](/model/content-type.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 404              | NotFound            | [Error](/key-concepts/errors.md)       |
| 409              | NotLatestVersion    | [Error](/key-concepts/errors.md)       |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |

## Validations

| Type | Description |
|-|-|
| Id does not exist | The content type must be unique for the project |
| Project does not exist | The content type must be unique for the project |
