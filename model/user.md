---
description: A user resource contains profile and workflow details for a user.
---
# User

A user resource contains profile and workflow details for a user. Extended profile properties for a user can be specified in the `custom` field

## Properties

| Name                          | Type     | Format                            | Description                                                                           |
|-------------------------------|----------|-----------------------------------|---------------------------------------------------------------------------------------|
| username                      | string   |                                   | The user's username                                                                   |
| email                         | string   |                                   | The user's email                                                                      |
| title                         | string   |                                   | The user's title, e.g. Mr, Mrs, Miss, Ms, Dr, etc.                                    |
| firstname                     | string   |                                   | The user's firstname                                                                  |
| lastname                      | string   |                                   | The user's lastname                                                                   |
| avatarUrl                     | string   | URI                               | The user's avatar image location                                                      |
| timezone                      | string   | Timezone offset name              | The user's timezone preference                                                        |
| language                      | string   | [Language code](/localization.md) | The user's language preference                                                        |
| custom.*                      | object   |                                   | Additional custom data stored against the user                                        |
| credentials                   | object   |                                   | Container for authentication details                                                  |
| credentials.password          | string   |                                   | The password value when creating a user.<br>The value is never returned in a response |
| sys                           | object   |                                   | Container for user system details                                                     |
| sys.id                        | string   | GUID                              | The user identifier as a 128 bit GUID.                                                |
| sys.status                    | object   |                                   | Container for status information                                                      |
| sys.status.active             | boolean  |                                   | A flag to indicate whether the user is active                                         |
| sys.status.deactivationReason | string   |                                   | Information on why the user was deactivated                                           |
| sys.status.locked             | boolean  |                                   | A flag to indicate whether the user is active                                         |
| sys.status.passwordExpired    | boolean  |                                   | A flag to indicate whether the user's password has expired                            |
| sys.status.passwordExpiry     | datetime |                                   | If a global policy is set, the date and time when the user's password will expire     |
| sys.created                   | datetime |                                   | The date and time the user was first created                                          |
| sys.modified                  | datetime |                                   | The date and time the user was modified                                               |
| sys.activated                 | datetime |                                   | The date and time the user was last activated                                         |
| sys.lastLogin                 | datetime |                                   | The date and time the user last logged-in                                             |
| sys.passwordChanged           | datetime |                                   | The date and time the user's password was last changed                                |



## Example

```json
{
    "username": "s.yearsley",
    "email": "s.yearsley@zengenti.com",
    "title": "Mr",
    "firstname": "Tyler",
    "lastname": "Durden",
    "avatarUrl": "https://mywebsite/users/tyler.jpg",
    "timezone": "America/New_York",
    "language": "en-GB",
    "custom": {
        "department": "finance",
    },
    "credentials": {
        "password": "pr0j3ctM4yh3m"
    },
    "sys": {
        "id": "e09e77b9-9dd9-4d46-b7dd-deb9702a5835",
        "status": {
            "active": true,
            "deactivationReason": null,
            "locked": false,
            "passwordResetRequired": false,
            "passwordExpiry": "2020-01-31 16:07:51"
        },
        "created": "2020-06-24T16:39:18.000Z",
        "modified": "2020-06-24T16:39:18.000Z",
        "activated": "2020-06-24T16:39:18.000Z",
        "lastLogin": "2020-06-24T16:39:18.000Z",
        "passwordChanged": "2020-06-24T16:39:18.000Z"
    }
}
```