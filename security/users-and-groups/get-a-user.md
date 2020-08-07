---
description: A user resource can be retrieved by it's GUID identifier
---

# Get a user by id

A user resource can be retrieved by any valid [UserIdentifier](/security/identifiers.md).

<span class="label label--get">GET</span> /api/management/security/users/**{userIdentifier}**

## Parameters

| Name           | Parameter type | Type                                       | Description                 |
| :------------- | :------------- | :----------------------------------------- | :-------------------------- |
| userIdentifier | path           | [UserIdentifier](/security/identifiers.md) | One of the user identifiers |

## Example requests

```http
GET: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

```http
GET: /api/management/security/users/tdurden
```

```http
GET: /api/management/security/users/t.durden@fightclub.com
```

## Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 200              | Success             | [User](/model/user.md)           |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
