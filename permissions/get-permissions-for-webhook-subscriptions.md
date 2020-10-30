## Get permissions for webhook subscriptions

Gets the webhook subscription permissions for the requested user.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/webhookSubscriptions?userId=**{userId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| userId | query | string | | The id of the user to retrieve permissions for.  |

### Example request

```http
GET: /api/management/projects/movieDb/security/permissionswebhookSubscriptions?userId=a.user
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | Array of actions available       |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

### Example response

```json
{
    "actions": ["create", "delete", "update", "view"]
}
```

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