---
description: Deletes a project resource.
---
# Delete a project

Deletes a project resource.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**

## Example request

```http
DELETE: /api/management/projects/movieDb/
```

### Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Project](/model/project.md)     |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | CannotBeDeleted     | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Single project

A project cannot be deleted if it is the only project in a Contensis instance. If you attempt to delete all projects in a Contensis instance, you will get the following response.

```json
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

```json
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
