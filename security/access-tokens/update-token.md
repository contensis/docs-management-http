---
description: Updates an existing API access token.
---

# Update an API access token

Updates an existing API access token.

<span class="label label--put">PUT</span> /api/management/security/accessTokens/**{accessTokenId}**

## Example request

```json
PUT: /api/management/security/accessTokens/8f3dad0f-9ac3-450f-a825-0457542c04c7

{
    "id": "8f3dad0f-9ac3-450f-a825-0457542c04c7",
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": false,
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
| 200              | OK                  | [AccessToken](/model/access-token.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)      |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)      |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)      |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)      |