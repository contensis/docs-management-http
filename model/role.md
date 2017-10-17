# Roles

An role definition in the Management API contains a list of permissions and the content types or entries those permissions are valid for. The role also contains a list of users and groups who will be given those permissions.

### Role

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | GUID | The entry identifier as a 128 bit GUID. |
| name | object | [Localized value](/key-concepts/localization.md) | The name of the role. |
| description | object | [Localized value](/key-concepts/localization.md) | The description of the role. |
| enabled | boolean | | If true then this role is enabled, otherwise false. |
| permissions | object | [Permissions](#permissions) | Permissions to be assigned by the role. |
| assignments | object | [Assignments](#assignments) | Assignments to be given the roles permissions. |

### Permissions

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| entries | array | [Permission](#permission) | An array of permissions for entries. |
| contentTypes | array | [Permission](#permission) | An array of permissions for contentTypes. |

### Permission
| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | GUID | The content type identifier as a 128 bit GUID. |
| languages | array | string | One or more languages to give permission for, use * for all languages. |
| actions | array | string | One or more actions to give permission for, use * for all actions, or stateName.* for all permissions in a given state. |

### Assignments
| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| users | array | string | Zero or more user names. |
| groups | array | string | Zero or more group names. |

## Example

This JSON example shows a role that gives permissions to the movie content type.

```json
{
    "id": "34f503ca-fd44-4d47-b86a-c9d94c4d5d54",
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
