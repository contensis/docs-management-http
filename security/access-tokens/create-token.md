---
description: Creates a new API access token.
---

# Create an API access token

Creates a new API access token for one or more projects

<span class="label label--post">POST</span> /api/management/security/accessTokens/

## Example request

```json
POST: /api/management/security/accessTokens/

{
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": true,
    "scopes": [
        "website_delivery",
        "website_management",
        "internal_delivery"
    ]
}
```

### Response message

| HTTP status code | Reason              | Response model                        |
|:-----------------|:--------------------|:--------------------------------------|
| 201              | Created             | [AccessToken](/model/access-token.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)      |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)      |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)      |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)      |