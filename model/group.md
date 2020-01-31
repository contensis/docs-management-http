---
description: A group resource contains references to users and child groups that form membership of the group.
---
# Group

A group resource contains references to users and child groups that form membership of the group.

## Properties

| Name         | Type     | Format | Description                                        |
|--------------|----------|--------|----------------------------------------------------|
| name         | string   |        | The unique group name                              |
| description  | string   |        | A description for the purpose of the group         |
| type         | string   |        | The type of group - 'sys', 'contensis', 'external' |
| custom.*     | object   |        | Custom string properties for the group             |
| adminUserId  | string   | GUID   | The admin user identifier                          |
| adminGroupId | string   | GUID   | The admin group identifier                         |
| sys.id       | string   | GUID   | The group identifier as a 128 bit GUID.            |
| sys.created  | datetime |        | The group identifier as a 128 bit GUID.            |
| sys.modified | datetime |        | The group identifier as a 128 bit GUID.            |

## Example

```json
{
    "name": "Paper Street Soap Company",
    "Description": "Employees of the Paper Street Soap Company", 
    "type": "contensis",
    "custom" : {
        "clientId": "PSSC"
    },
    "adminUserId": "7c0b186e-94bc-4bde-8a9d-07d2bfa4139d",
    "adminGroupId": "9c768b00-cc74-4d8d-8cee-bc65b52c152b",
    "sys": {
        "id": "236f1ce9-e5e6-4a93-b178-d52f2f723428",
        "created": "2020-01-31 15:26:54",
        "modified": "2020-01-31 15:27:00"
    }
}
```