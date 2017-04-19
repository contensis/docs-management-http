# Projects

## Get a project

Gets an existing project by the project id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**

### Example request

```http
GET: /api/management/projects/movieDb/
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Project](/model/project.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | Project not found | [Error](/key-concepts/errors.md) |
| 500 | Internal server error | [Error](/key-concepts/errors.md) |



## Create a project

Creates a new project resource.

<span class="label label--post">POST</span> /api/management/projects/

### Example request

```http
POST: /api/management/projects/

{
    "id": "movieDb",
    "name": "Movie database",
    "description": "A source of movie and TV series",
    "primaryLanguage": "en-GB",
    "supportedLanguage": [
        "en-GB",
        "fr-FR",
        "de-DE"
    ]
}
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | [Project](/model/project.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 409 | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

**TODO: Add validation responses**

### Validations

| Type | Description |
|-|-|
| Non-unique id | The project must be unique for the instance of Contensis |
| Primary language is required | A primary language must be specified |

### Remarks

If the *primaryLanguage* value is not included in the *supportedLanguages* array then it will automatically be added by the service when the project is created.


## Update a project

Updates an existing project resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**

### Example request

```http
PUT: /api/management/projects/movieDb

{
    "id": "movieDb",
    "name": "Movie database",
    "description": "A source of movie and TV series",
    "primaryLanguage": "en-GB",
    "supportedLanguage": [
        "en-GB",
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
| 404 | Project not found | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | Internal server error | [Error](/key-concepts/errors.md) |


**TODO: Add validation responses**





## List projects

Returns a list of the project resources for a Contensis instance.

<span class="label label--get">GET</span> /api/management/projects/

### Example request

```http
GET: /api/management/projects/
```


### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Project [...]](/model/project.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |





## Delete a project

Deletes a project resource.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**

### Example request

```http
DELETE: /api/management/projects/movieDb/
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Project](/model/project.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | CannotBeDeleted | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

**TODO: Add validation responses**

### Validations

| Type | Description |
|-|-|
| Single project | A project cannot be deleted if it is the only project |