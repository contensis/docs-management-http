---
description: Role definitions in the Management API contain permissions associated with entries, assets, and webhook subscriptions, and with users and groups assigned to those permissions.
---
# Roles

Role definitions in the Management API contain permissions associated with entries, assets, and webhook subscriptions, and with users and groups assigned to those permissions.

### Role

| Name        | Type    | Format                                           | Description                                            |
|-------------|---------|--------------------------------------------------|--------------------------------------------------------|
| id          | string  | GUID                                             | The role identifier as a 128 bit GUID.                 |
| name        | object  | [Localized value](/key-concepts/localization.md) | The name of the role.                                  |
| description | object  | [Localized value](/key-concepts/localization.md) | The description of the role.                           |
| enabled     | boolean |                                                  | If true then this role is enabled, otherwise false.    |
| permissions | object  | [Permissions](#permissions)                      | Permissions associated with content types and entries. |
| assignments | object  | [Assignments](#assignments)                      | Assignments of users and user groups to the role.      |

### Permissions

| Name         | Type  | Format                    | Description                               |
|--------------|-------|---------------------------|-------------------------------------------|
| entries      | array | [Entry/asset permission](#entryassetpermission) | An array of permissions for entries.      |
| assets | array | [Entry/asset permission](#entryassetpermission) | An array of permissions for assets. |
| webhookSubscription | object | [Webhook subscription permissions](#webhooksubscriptionpermissions) | Permissions for webhook subscriptions. |

### Entry/asset permission <a id="entryassetpermission"></a>

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | GUID | The content type identifier as a 128 bit GUID. |
| languages | array | string | One or more languages to give permissions to. * denotes all languages. |
| actions | array | string | One or more actions to give permission to. * denotes all actions.<br> **{workflowStateName}**.&#42; denotes all permissions applicable to the given workflow state. |

### Webhook subscription permissions <a id="webhooksubscriptionpermissions"></a>

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| actions | array | string | One or more actions to give permission for webhook subscriptions. The possible values are: **create**, **update**, **delete**, **view**. |

### Assignments

| Name    | Type  | Format | Description                 |
|---------|-------|--------|-----------------------------|
| users   | array | string | Zero or more user names.    |
| groups  | array | string | Zero or more group names.   |
| apiKeys | array | string | Zero or more API key names. |

## Example

This JSON example shows a role that gives authoring permissions for the user group "Movie Editors", and the user "a.user" to movie content type entries for the en-GB language code, all permissions for all assets, and create and view permissions for webhook subscriptions.

```json
{
    "id": "34f503ca-fd44-4d47-b86a-c9d94c4d5d54",
    "name": {
        "en-GB": "Movie Editors"
    },
    "description": {
        "en-GB": "Movie editors can edit movie entries, but not submit or approve them"
    },
    "enabled": true,
    "permissions": {
        "entries": [
            {
                "id": "movie",
                "languages": [
                    "en-GB"
                ],
                "actions": [
                    "sys.update",
                    "draft.*",
                    "awaitingApproval.revoke"
                ]
            }
        ],
        "assets": [{
                "id": "*",
                "languages": ["*"],
                "actions": ["contensisEntryBasic.*"]
            }
        ],
        "webhookSubscription": {
            "actions": [ "create", "view" ]
        }
    },
    "assignments": {
        "users": [
            "f.haygood"
        ],
        "groups": [
            "Movie Editors"
        ],
        "apiKeys": [
            "Movie Import"
        ]
    }
}
```
