---
description: Creates a new access token for a specific API key.
---

# Create an access token

Creates a new access token for a specific API key.

<span class="label label--post">POST</span> /api/management/security/apiKeys/**{apiKeyId}**/accessTokens

## Example request

```json
POST: /api/management/security/apiKeys/551bcd98-fba5-43b7-95cf-c3e0abc540c1/accessTokens

{
    "name": "Development token"
}
```

### Response message

| HTTP status code | Reason              | Response model                         |
|:-----------------|:--------------------|:---------------------------------------|
| 201              | Created             | [Access token](/model/access-token.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)       |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |