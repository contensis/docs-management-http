# Get authorization for a webhook subscription action

Gets an authorization confirmation for the requested user and webhook subscription action.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/webhookSubscriptions/actions/**{action}**?userId=**{userId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| action | path | string | | Name of the action to check authorization for. |
| userId | query | string | | The optional id of the user to check authorization for.  |

### Example request

```http
GET: /api/management/projects/movieDb/security/permissionswebhookSubscriptions/actions/create/?userId=a.user
```

### Response message

| HTTP status code | Reason                    | Response model                   |
|:-----------------|:--------------------------|:---------------------------------|
| 200              | The action is authorized  | Authorized true                  |
| 404              | Not authorized for action | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError       | [Error](/key-concepts/errors.md) |

### Example response

```json
{
    "authorized": true
}
```