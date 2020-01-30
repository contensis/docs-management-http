---
description: A group resource contains references to users and child groups that form membership of the group.
---
# Group

A group resource contains references to users and child groups that form membership of the group.

## Properties

| Name        | Type   | Format | Description                                        |
|-------------|--------|--------|----------------------------------------------------|
| name        | string |        | The unique group name                              |
| description | string |        | A description for the purpose of the group         |
| type        | string |        | The type of group - 'sys', 'contensis', 'external' |
| sys.id      | string | GUID   | The group identifier as a 128 bit GUID.            |




## Example

```json
{
    "name": "Paper Street Soap Company",
    "Description": "Employees of the Paper Street Soap Company", 
    "type": "contensis",
    "custom" : {
        "clientId": "PSSC"
    },
    "sys": {
        "id": "236f1ce9-e5e6-4a93-b178-d52f2f723428"
    }
}
```