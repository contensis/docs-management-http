## Delete a role

Deletes an role by its Id.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/roles/**{roleId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |
| roleId | path | string | GUID | The role identifier. |

### Example request

```http
Accept: application/json
DELETE: /api/management/projects/movieDb/roles/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 204 | Success | |
| 403 | Forbidden | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |