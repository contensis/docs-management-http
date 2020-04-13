---
description: Gets a existing API key.
---

# Get an API key

Gets a existing API key.

<span class="label label--get">GET</span> /api/management/security/apiKeys/**{apiKeyId}**

## Parameters

| Name     | Parameter type | Type   | Format | Description                 |
|----------|:---------------|:-------|:-------|:----------------------------|
| apiKeyId | path           | string | Guid   | The API key identifier |

## Example request

```http
GET: /api/management/security/apiKeys/551bcd98-fba5-43b7-95cf-c3e0abc540c1
```

### Response message

| HTTP status code | Reason              | Response model                        |
|:-----------------|:--------------------|:--------------------------------------|
| 200              | OK                  | [API key](/model/api-key.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)      |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)      |
| 404              | NotFound            | [Error](/key-concepts/errors.md)      |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)      |