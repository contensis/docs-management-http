# Projects
Projects offer a way of grouping related content types, entries and assets. Typically a project would represent a single application such as a website, intranet or mobile application.

Projects are a licensed feature and the number you can create will depend on which license you have purchased.


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
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |



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
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Non-unique id 
A project must have a unique id. If you attempt to create a project with an id which is already in use you will get the following response.

```http
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

```http
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
| 404 | NotFound | [Error](/key-concepts/errors.md) |
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

### Validations

#### Single project
A project cannot be deleted if it is the only project in a Contensis instance. If you attempt to delete all projects in a Contensis instance, you will get the following response.

```http
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors deleting the project 'movieDb'",
    "data": [
        {
            "field": "",
            "message": "The specified project is the only project and therefore cannot be deleted"
        }
    ],
    "type": "Validation"
}
```

#### A project containing content
In order to delete a project it has to be empty. This is a safeguard to stop people deleting projects which are in use. If you attempt to delete a project which contains content types, you will get the following response.

```http
{
    "logId": "5fca7986-5ba3-4eb4-9cea-b5f25aaaed09",
    "message": "There are validation errors deleting the project 'movieDb'",
    "data": [
        {
            "field": "",
            "message": "The project has associated content types so cannot be deleted"
        }
    ],
    "type": "Validation"
}
```
