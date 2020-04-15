---
description: Creates a new flow for a specific API key.
---

# Create a flow

Creates a new flow for a specific API key.

<span class="label label--post">POST</span> /api/management/security/apiKeys/**{apiKeyId}**/flows

## Example - Create a client credential flow

```json
POST: /api/management/security/apiKeys/551bcd98-fba5-43b7-95cf-c3e0abc540c1/flows

{
    "grantType": "clientCredential",
    "clientId": "mainWebsite"
}
```

## Example - Create an access token flow

```json
POST: /api/management/security/apiKeys/551bcd98-fba5-43b7-95cf-c3e0abc540c1/flows

{
    "grantType": "accessToken",
}
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | Created             |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |