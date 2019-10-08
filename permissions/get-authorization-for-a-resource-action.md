# Get authorization for a resource action

Gets an authorization confirmation for the requested user, resource and action.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/**{resourceType}**/**{resourceId}**/actions/**{action}**?userId=**{userId}**&language=**{language}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| resourceType | path | string |  | The type of resource to retrieve permissions for. Contenttypes or entries. |
| resourceId | path | GUID | | Id of the resource to retrieve permissions for.  |
| action | path | string | | Name of the action to check authorization for. |
| userId | query | string | | The optional id of the user to check authorization for.  |
| language | query | string | [LanguageCode](/key-concepts/localization.md) | The optional language code to check authorization for.  |

### Example request

```http
GET: /api/management/projects/movieDb/security/permissions/entries/a65a9d9d-ee64-4c25-a80c-ab5aee00fb9d/actions/sys.create/?userId=a.user
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