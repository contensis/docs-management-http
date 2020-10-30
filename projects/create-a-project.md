---
description: Creates a new project resource.
---
## Create a project

Creates a new project resource.

<span class="label label--post">POST</span> /api/management/projects/

### Example request

```json
POST: /api/management/projects/

{
    "id": "movieDb",
    "name": "Movie database",
    "description": "A source of movie and TV series",
    "primaryLanguage": "en-GB",
    "supportedLanguage": [
        "fr-FR",
        "de-DE"
    ]
}
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 201              | Created               | [Project](/model/project.md)     |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | NotFound              | [Error](/key-concepts/errors.md) |
| 409              | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422              | ValidationError       | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |

### Validations

#### Non-unique id

A project must have a unique id. If you attempt to create a project with an id which is already in use you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the project",
    "data": [
        {
            "field": "",
            "message": "A project with this Id already exists"
        }
    ],
    "type": "Validation"
}
```

#### Primary language is required

A project must have a primary language defined. If you attempt to create a project without specifying a primary language you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the project",
    "data": [
        {
            "field": "Project",
            "message": "The primary language code is not valid"
        }
    ],
    "type": "Validation"
}
```

#### Maximum id length

The id of the project cannot be longer than 40 characters.

#### Maximum name length

The name of the project cannot be longer than 40 characters.

### Remarks

If the *primaryLanguage* value is not included in the *supportedLanguages* array then it will automatically be added by the service when the project is created.
