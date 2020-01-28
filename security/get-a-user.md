---
description: A user resource can be retrieved by it's GUID identifier
---

## Get a user by id

A user resource can be retrieved by it's GUID identifier.

<span class="label label--get">GET</span> /api/management/security/users/**{userId}**

### Parameters

| Name   | Parameter type | Type   | Format | Description          |
|:-------|:---------------|:-------|:-------|:---------------------|
| userId | path           | string | GUID   | The user identifier. |

### Example request

```http
GET: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

---

## Get a user by username

A user resource can be retrieved by it's username.

<span class="label label--get">GET</span> /api/management/security/users/**{username}**

### Parameters

| Name     | Parameter type | Type   | Format | Description               |
|:---------|:---------------|:-------|:-------|:--------------------------|
| username | path           | string |        | The username of the user. |

### Example request

```http
GET: /api/management/security/users/tdurden
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

---

## Get a user by email

A user resource can be retrieved by it's email address.

<span class="label label--get">GET</span> /api/management/security/users/**{username}**

### Parameters

| Name  | Parameter type | Type   | Format | Description            |
|:------|:---------------|:-------|:-------|:-----------------------|
| email | path           | string |        | The email of the user. |

### Example request

```http
GET: /api/management/security/users/t.durden@fightclub.com
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |