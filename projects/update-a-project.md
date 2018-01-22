---
description: Updates an existing project resource.
---
## Update a project

Updates an existing project resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**

### Example request

```json
PUT: /api/management/projects/movieDb

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

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Project](/model/project.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Remarks

It is not possible to update the Id once you've created a project.
