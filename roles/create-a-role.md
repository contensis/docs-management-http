## Create a Role

Creates a new role.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/security/roles

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |

### Example request

```json
POST: /api/management/projects/movieDb/security/roles/

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
                "actions": ["sys.update", "awaitingApproval.revoke"]
            }
        ],
        "contentTypes": [ ]
    },
    "assignments": {
        "users": [ "a.user" ],
        "groups": [ "Movie Editors" ],
        "apiKeys": [ "Movie Import" ]
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

Roles are project specific. If you attempt to create a role in a project which does not exist you will get the following response. 

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

#### Insufficient permissions to create a role

In order to create a role you must be a member of the "System Administrators" user group. If you do not have permission to create a role you will get the following response.

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

The content type must exist to be able to create a role. If you attempt to create a role for a content type which does not exist you will get the following response.

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