## List roles
List roles by project Id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/roles

### Parameters

| Name      | Parameter type | Type   | Format  | Description                                                                                             |
|:----------|:---------------|:-------|:--------|:--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |         | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| pageIndex | query          | number | integer | The index of the page                                                                                   |
| pageSize  | query          | number | integer | The number of results per page. The default is 25.                                                      |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/security/roles?pageIndex=1&pageSize=5
```

### Response message

| HTTP status code | Reason              | Response model                          |
|:-----------------|:--------------------|:----------------------------------------|
| 200              | Success             | [PagedList&lt;Role&gt;](/model/role.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)        |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)        |
| 404              | NotFound            | [Error](/key-concepts/errors.md)        |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)        |

### Validations

#### Project does not exist

Roles are project specific. If you attempt to list roles in a project which does not exist you will get the following response. 

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors listing the roles",
    "data": [
        {
            "field": "projectId",
            "message": "The project does not exist"
        }
    ],
    "type": "Validation"
}
```

#### Insufficient permissions to list roles

In order to list roles you must be a member of the "System Administrators" user group. If you do not have permission to list roles you will get the following response.

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There are validation errors listing the roles",
    "data": [
        {
            "message": "Access denied"
        }
    ],
    "type": "Validation"
}
```