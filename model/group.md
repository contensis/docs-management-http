---
description: A group resource contains references to users and child groups that form membership of the group.
---
# Group

A group resource contains references to users and child groups that form membership of the group.

## Properties

| Name        | Type     | Format | Description                                  |
|-------------|----------|--------|----------------------------------------------|
| id          | string   | GUID   | The group identifier as a 128 bit GUID.      |
| name        | string   |        | The unique group name                        |
| description | string   |        | A description for the purpose of the group   |
| type        | string   |        | The type of group - 'system', 'custom', 'AD' |
| users       | string[] | GUID   | An array of assigned user ids                |
| groups      | string[] | GUID   | An array of child groups ids                 |

## Example

```json
{
    "id": "236f1ce9-e5e6-4a93-b178-d52f2f723428",
    "name": "Developers",
    "Description": "Developers working in Zengenti",
    "users": [
        "e09e77b9-9dd9-4d46-b7dd-deb9702a5835",
        "71c46a08-c732-4eb8-86fa-e5b7397a6c5b",
        "b9acfe36-398a-4034-89fd-807609615de9",
        "ee82c924-dd40-461f-bb49-e3c36797b21e"
    ],
    "groups": [
        "250840b9-7834-4a8c-8207-119f98205ff0"
    ]
}
```