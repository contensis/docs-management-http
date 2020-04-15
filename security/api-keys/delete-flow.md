---
description: Deletes an existing API key flow.
---

# Delete an access token

Deletes an existing API key flow.

<span class="label label--delete">DELETE</span> /api/management/security/apiKeys/**{apiKeyId}**/flows/**{flowId}**

## Parameters

| Name     | Parameter type | Type   | Format | Description            |
|----------|:---------------|:-------|:-------|:-----------------------|
| apiKeyId | path           | string | Guid   | The API key identifier |
| flowId   | path           | string | Guid   | The flow identifier    |

## Example request

```http
DELETE: /api/management/security/apiKeys/8f3dad0f-9ac3-450f-a825-0457542c04c7/flows/4a2715c6-3a0a-4cb7-9ba6-a581a5c4701f
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | NoContent           |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |