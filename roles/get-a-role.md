## Get a role

Gets a role by its Id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| roleId | path | string | GUID | The role identifier. |

### Example request

```http
GET: /api/management/projects/movieDb/security/roles/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Role](/model/role.md) |
| 403 | Forbidden | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations

#### Project does not exist

Roles are project specific. If you attempt to get a role in a project which does not exist you will get the following response. 

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors getting the role",
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

If you attempt to get a role which does not exist you will get the following response. 

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors getting the role",
    "data": [
        {
            "field": "projectId",
            "message": "The role with id '71f73a9b-2a13-4d63-bcc1-e8ee5047b01c' does not exist"
        }
    ],
    "type": "Validation"
}
```

#### Insufficient permissions to get a role

In order to get a role you must be a member of the "System Administrators" user group. If you do not have permission to get a role you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors getting the role",
    "data": [
        {
            "message": "Access denied"
        }
    ],
    "type": "Validation"
}
```