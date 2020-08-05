## Delete a user

Deleting a user can be done by sending a DELETE request to the user resource location.

<span class="label label--delete">DELETE</span> /api/management/security/users/**{userIdentifier}**

### Parameters

| Name           | Parameter type | Type   | Format   | Description                       |
| :------------- | :------------- | :----- | :------- | :-------------------------------- |
| userIdentifier | path           | string | GUID     | The user id as the identifier.    |
| userIdentifier | path           |        | Username | The username as the identifier.   |
| userIdentifier | path           |        | Email    | The user email as the identifier. |

### Example requests

```http
DELETE: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

```http
DELETE: /api/management/security/users/tdurden
```

```http
DELETE: /api/management/security/users/t.durden@fightclub.com
```

## Remarks

This action requires system administration privileges.

### Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
