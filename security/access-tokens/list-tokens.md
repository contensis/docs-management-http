---
description: Lists all API access tokens for all projects.
---

# List API access tokens

Lists all API access tokens for all projects.

<span class="label label--get">GET</span> /api/management/security/accessTokens/


## Example request

```http
GET: /api/management/security/accessTokens/
```

### Response message

| HTTP status code | Reason              | Response model                                         |
|:-----------------|:--------------------|:-------------------------------------------------------|
| 200              | OK                  | PagedList&lt;[AccessToken](/model/access-token.md)&gt; |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)                       |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)                       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)                       |