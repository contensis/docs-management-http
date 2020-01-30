---
description: A group resource contains references to users and child groups that form membership of the group.
---
# Group

A group resource contains references to users and child groups that form membership of the group.

## Properties

| Name                | Type   | Format | Description                                        |
|---------------------|--------|--------|----------------------------------------------------|
| id                  | string | GUID   | The group identifier as a 128 bit GUID.            |
| type                | string |        | The type of group - 'sys', 'contensis', 'external' |
| profile.name        | string |        | The unique group name                              |
| profile.description | string |        | A description for the purpose of the group         |



## Example

```json
{
    "id": "236f1ce9-e5e6-4a93-b178-d52f2f723428",
    "type": "contensis",
    "profile": {
        "name": "Paper Street Soap Company",
        "Description": "Employees of the Paper Street Soap Company", 
        "custom" : {
            "clientId": ""
        }
    }
}
```