---
description: Deletes an existing API access token.
---

# Delete an API access token

Deletes an existing API access token.

<span class="label label--delete">DELETE</span> /api/management/security/accessTokens/**{accessTokenId}**

## Example request

```http
DELETE: /api/management/security/accessTokens/8f3dad0f-9ac3-450f-a825-0457542c04c7
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | NoContent           |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |