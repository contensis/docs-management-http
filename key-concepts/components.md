# Components

## Create a component

Creates a new component resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/components/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |

### Example request

```http
POST: /api/management/projects/movieDb/components/

{
    "id": "socialCard",
    "projectId": "movieDb",
    "name": {
        "en-GB": "Social Card"
    },
    "description": {
        "en-GB": "A Social Media Card"
    },
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
                    "en-GB": "The title of the social media card"
                },
                "properties": {
                    "placeholderText": {
                        "en-GB": "Enter the title to be displayed as part of the card"
                    }
                }
            }
        },
        {
            "id": "description",
            "name": {
                "en-GB": "Description"
            },
            "dataType": "string",
        },
        {
            "id": "image",
            "name": {
                "en-GB": "Image"
            },
            "dataType": "objectArray",
            "dataFormat": "asset",
            "validations": {
                "allowedContentTypes": {
                    "contentTypes": ["image"]
                }
            }
        }
    ],
    "workflowId": "ContensisDefault",
    "dataFormat": "component"
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | [Content Type](/model/content-type.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | Conflict | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
**TODO: Add validation responses**

### Validations

| Type | Description |
|-|-|
| Project does not exist | A project must exist to be able to create components |
| Non-unique id | The content type or component must be unique for the project |

### Remarks