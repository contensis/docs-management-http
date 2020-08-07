---
description: For convenience, Users and Groups can be identified in various ways.
---

# User and Group Identifiers

For convenience, [User](/model/user.md) and [Group](/model/group.md) objects can be identified by using one of several identifiers.

For example, a [User](/model/user.md) can be identified by Username, Id or Email Address. A [Group](/model/group.md) can be identified by Name or Id.

A combination of identifiers can be used if an endpoint requires both types of object.

## Available User Identifiers

| Identifier    | Format | Description                          |
| :------------ | :----- | :----------------------------------- |
| Id            | GUID   | The user Id                          |
| Username      | string | The user Username                    |
| Email address | string | The user email in valid email format |

## Available Group Identifiers

| Identifier | Format | Description    |
| :--------- | :----- | :------------- |
| Id         | Guid   | The group Id   |
| Name       | string | The group name |

## Example requests

#### User requests

```http
GET: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

```http
GET: /api/management/security/users/tdurden
```

```http
GET: /api/management/security/users/t.durden@fightclub.com
```

#### Group requests

```http
GET: /api/management/security/groups/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

```http
GET: /api/management/security/groups/Paper%20Street%20Soap%20Company
```

#### Combination requests

```http
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/9f02a3d1-d8eb-4b10-8ed6-293a11d5201f
```

```http
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/tdurden
```

```http
HEAD: /api/management/security/groups/9bb89380-fd49-41a5-ab2f-fc25e482a251/users/tdurden@fightclub.com
```

```http
HEAD: /api/management/security/groups/Paper%20Street%20Soap%20Company/users/3d063773-2ca9-4baf-90e1-ed674fa68640
```
