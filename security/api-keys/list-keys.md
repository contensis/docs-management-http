---
description: Lists all API keys.
---

# List API access tokens

Lists all API keys.

<span class="label label--get">GET</span> /api/management/security/apiKeys/


## Example request

```http
GET: /api/management/security/apiKeys/
```

### Response message

| HTTP status code | Reason              | Response model                                |
|:-----------------|:--------------------|:----------------------------------------------|
| 200              | OK                  | PagedList&lt;[Api key](/model/api-key.md)&gt; |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)              |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)              |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)              |