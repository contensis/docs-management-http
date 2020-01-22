---
description: Creates a new component resource.
---

# Create a component

Creates a new component resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/components/

# Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |

## Example request

```json
POST: /api/management/projects/movieDb/components/

{
    "id": "movieRole",
    "projectId": "website",
    "name": {
        "en-GB": "Movie role"
    },
    "description": {
        "en-GB": "A Persons role within a movie"
    },
    "fields": [
        {
            "id": "person",
            "name": {
            "en-GB": "Person"
            },
            "dataType": "object",
            "dataFormat": "entry",
            "description": {
                "en-GB": "The actor or crew member"
            },
            "default": {},
            "validations": {
                "allowedContentTypes": {
                    "contentTypes": ["person"]
                }
            },
            "editor": {
                "id": "entry",
                "instructions": {
                    "en-GB": ""
                },
                "properties": {
                    "placeholderText": {
                        "en-GB": ""
                    }
                }
            }
        },
        {
            "id": "role",
            "name": {
                "en-GB": "Role"
            },
            "dataType": "String",
            "dataFormat": null,
            "description": {},
            "default": {},
            "validations": null,
            "editor": null
        }
    ],
    "workflowId": "ContensisDefault",
    "dataFormat": "component",
    "version": {
        "createdBy": "s.derrickson",
        "created": "2016-10-12T09:29:18.5144641+01:00",
        "modifiedBy": "b.cumberbatch",
        "modified": "2016-10-13T10:15:12.1973648+01:00",
        "publishedBy": "b.cumberbatch",
        "published": "2016-10-13T10:15:12.1973648+01:00",
        "versionNo": "0.2"
    }
}
```

## Response message

| HTTP status code | Reason              | Response model                         |
|:-----------------|:--------------------|:---------------------------------------|
| 201              | Created             | [Content Type](/model/component.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 404              | NotFound            | [Error](/key-concepts/errors.md)       |
| 409              | Conflict            | [Error](/key-concepts/errors.md)       |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |

## Validations

### Project does not exist

A project must exist to be able to create a component. If you specify a project which doesn't exist you will get the following response.

```json
{
    "logId": "694b56b4-bdd9-4330-9b48-a32047037a0a",
    "message": "Unknown project 'movieDb'",
    "data": [
        {
            "field": "projectId",
            "message": "A project with the Id 'movieDb' does not exist"
        }
    ],
    "type": "Validation"
}
```

### Non-unique id

The Id given to a component must be unique. If there is an existing component or content type with the same Id then you will get the following response.

```json
{
    "logId": "ea13ba29-33f4-423c-9789-5c94b978e03f",
    "message": "There are validation errors creating the component",
    "data": [
        {
            "field": "id",
            "message": "A content type or component with this Id already exists"
        }
    ],
    "type": "Validation"
}

```

## Remarks
