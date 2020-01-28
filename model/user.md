---
description: A user resource contains profile and workflow details for a user.
---
# User

A user resource contains profile and workflow details for a user. Extended profile properties for a user can be specified in the `profile.extended` field

## Properties

| Name               | Type     | Format                              | Description                                            |
|--------------------|----------|-------------------------------------|--------------------------------------------------------|
| id                 | string   | GUID                                | The user identifier as a 128 bit GUID.                 |
| status             | string   | [UserStatus](/model/user-status.md) | The status for the user resource                       |
| created            | datetime |                                     | The date and time the user was first created           |
| activated          | datetime |                                     | The date and time the user was last activated          |
| lastLogin          | datetime |                                     | The date and time the user last logged-in              |
| passwordChanged    | datetime |                                     | The date and time the user's password was last changed |
| profile.username   | string   |                                     | The user's username                                    |
| profile.email      | string   |                                     | The user's email                                       |
| profile.title      | string   |                                     | The user's title, e.g. Mr, Mrs, Miss, Ms, Dr, etc.     |
| profile.firstname  | string   |                                     | The user's firstname                                   |
| profile.lastname   | string   |                                     | The user's lastname                                    |
| profile.avatarUrl  | string   | URI                                 | The user's avatar image location                       |
| profile.timezone   | string   | Timezone offset                     | The user's timezone preference                         |
| profile.language   | string   | [Language code](/localization.md)   | The user's language preference                         |
| profile.extended.* | object   |                                     | Additional custom data stored against the user         |


## Example

```json
{
    "id": "e09e77b9-9dd9-4d46-b7dd-deb9702a5835",
    "status": "active",
    "created": "2020-06-24T16:39:18.000Z",
    "activated": "2020-06-24T16:39:18.000Z",
    "lastLogin": "2020-06-24T16:39:18.000Z",
    "passwordChanged": "2020-06-24T16:39:18.000Z",
    "profile": {
        "username": "s.yearsley",
        "email": "s.yearsley@zengenti.com",
        "title": "Mrs",
        "firstname": "Scott",
        "lastname": "Yearsley",
        "avatarUrl": "https://mywebsite/users/harry.jpg",
        "timezone": "America/New_York",
        "language": "en-GB",
        "extended": {
            "department": "finance",
        }
    },
    "credentials": {
    }
}
```