---
description: Creates a new API key to allow access to one or more project APIs.
---

# Create an API key

Creates a new API key to allow access to one or more project APIs.

<span class="label label--post">POST</span> /api/management/security/apiKeys/

## Example request

```json
POST: /api/management/security/apiKeys/

{
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": true,
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
| 201              | Created             | [Api key](/model/api-key.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)      |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)      |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)      |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)      |