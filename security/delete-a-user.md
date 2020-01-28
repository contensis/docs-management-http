## Delete a user

Deletes a user by its GUID Id.

<span class="label label--delete">DELETE</span> /api/management/security/users/**{userId}**

### Parameters

| Name   | Parameter type | Type   | Format | Description          |
|:-------|:---------------|:-------|:-------|:---------------------|
| userId | path           | string | GUID   | The user identifier. |

### Example request

```http
DELETE: /api/management/security/users/82f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

## Remarks

TODO: Details around permissions

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |