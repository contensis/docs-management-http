## Update a Role

Updates an existing role.

<span class="label label--post">PUT</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}**

### Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                             |
|:----------|:---------------|:-------|:-------|:--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| roleId    | path           | GUID   |        | The role identifier.                                                                                    |

### Example request

```json
PUT: /api/management/projects/movieDb/security/roles/71b48d24-7f65-457d-bd51-cba977b74b74

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
                "languages": ["*"],
                "actions": ["draft.*", "awaitingApproval.revoke"]
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

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Role](/model/role.md)           |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Project does not exist

Roles are project specific. If you attempt to update a role in a project which does not exist you will get the following response. 

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors updating the role",
    "data": [
        {
            "field": "projectId",
            "message": "The project does not exist"
        }
    ],
    "type": "Validation"
}
```

#### Role does not exist

If you attempt to update a role which does not exist you will get the following response. 

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors updating the role",
    "data": [
        {
            "field": "projectId",
            "message": "The role with id '71b48d24-7f65-457d-bd51-cba977b74b74' does not exist"
        }
    ],
    "type": "Validation"
}
```

#### Insufficient permissions to update a role

In order to update a role you must be a member of the "System Administrators" user group. If you do not have permission to update a role you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors updating the role",
    "data": [
        {
            "message": "Access denied"
        }
    ],
    "type": "Validation"
}
```

#### Content type does not exist

The content type must exist to be able to update a role. If you attempt to update a role for a content type which does not exist you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors updating the role",
    "data": [
        {
            "field": "entries[index].id",
            "message": "The content type 'movie' does not exist"
        }
    ],
    "type": "Validation"
}
```

#### Language unsupported by the content type

Language assignments for a content type id must be supported by the content type. If you attempt to update a role with a language which is not supported by the content type you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors creating the role",
    "data": [
        {
            "field": "Role.Permissions.Entries[index]",
            "message": "The languages 'cy', 'fr' specified in the role are not supported by the content type."
        }
    ],
    "type": "Validation"
}
```