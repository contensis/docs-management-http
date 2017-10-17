## Create a Role

Creates a new role.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/roles/

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |

### Example request

```json
POST: /api/management/projects/movieDb/roles/

{
    "name": {
        "en-GB": "Movie Editors"
    },
    "description": {
        "en-GB": "Movie editors can edit movies, but not submit or approve them"
    },
    "enabled": true,
    "permissions": {
        "entries": [
            {
                "id": "movie",
                "languages": ["en-GB"],
                "actions": ["authoring.*", "awaitingApproval.revoke"]
            }
        ],
        "contentTypes": [ ]
    },
    "assignments": {
        "users": [ "a.user" ],
        "groups": [ "MovieEditors" ]
    }
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | [Role](/model/role.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | Forbidden | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Project does not exist

A project must exist to be able to create roles. If you attempt to create an role in a project which doesn't exist you will get the following response. 

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the role",
    "data": [
        {
            "field": "projectId",
            "message": "The project does not exist"
        }
    ],
    "type": "Validation"
}
```

#### None System Admin

In order to create a role you must be a system administrator, if you are not the following error will be returned

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the role",
    "data": [
        {
            "message": "Access denied"
        }
    ],
    "type": "Validation"
}
```

#### Content type does not exist

The content type must exist to be able to create an role. If you attempt to create an role for a content type which doesn't exist you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the role",
    "data": [
        {
            "field": "entries[index].id",
            "message": "The content type 'movie' does not exist"
        }
    ],
    "type": "Validation"
}
```