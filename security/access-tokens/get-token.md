---
description: Gets a existing API access token.
---

# Get an API access token

Gets a existing API access token.

<span class="label label--get">GET</span> /api/management/security/accessTokens/**{accessTokenId}**

## Parameters

| Name          | Parameter type | Type   | Format | Description                 |
|---------------|:---------------|:-------|:-------|:----------------------------|
| accessTokenId | path           | string | Guid   | The access token identifier |

## Example request

```http
GET: /api/management/security/accessTokens/551bcd98-fba5-43b7-95cf-c3e0abc540c1
```

### Response message

| HTTP status code | Reason              | Response model                        |
|:-----------------|:--------------------|:--------------------------------------|
| 200              | OK                  | [AccessToken](/model/access-token.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)      |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)      |
| 404              | NotFound            | [Error](/key-concepts/errors.md)      |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)      |