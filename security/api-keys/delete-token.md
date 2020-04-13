---
description: Deletes an existing API key access token.
---

# Delete an access token

Deletes an existing API key access token.

<span class="label label--delete">DELETE</span> /api/management/security/apiKeys/**{apiKeyId}**/accessTokens/**{accessTokenName}**

## Parameters

| Name            | Parameter type | Type   | Format | Description            |
|-----------------|:---------------|:-------|:-------|:-----------------------|
| apiKeyId        | path           | string | Guid   | The API key identifier |
| accessTokenName | path           | string |        | The access token name  |

## Example request

```http
DELETE: /api/management/security/apiKeys/8f3dad0f-9ac3-450f-a825-0457542c04c7/accessTokens/development
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | NoContent           |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |