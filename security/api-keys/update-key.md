---
description: Updates an existing API key.
---

# Update an API key

Updates an existing API key.

<span class="label label--put">PUT</span> /api/management/security/apiKeys/**{apiKeyId}**

## Example request

```json
PUT: /api/management/security/apiKeys/8f3dad0f-9ac3-450f-a825-0457542c04c7

{
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": false,
    "scopes": [
        "delivery_website",
        "management_website",
        "delivery_internal"
    ]
}
```

### Response message

| HTTP status code | Reason              | Response model                        |
|:-----------------|:--------------------|:--------------------------------------|
| 200              | OK                  | [Api key](/model/access-token.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)      |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)      |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)      |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)      |