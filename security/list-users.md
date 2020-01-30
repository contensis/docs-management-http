---
description: User resources can be retrieved as a paged list
---

## Get a user by id

User resources can be retrieved as a paged list and ordered by either username

<span class="label label--get">GET</span> /api/management/security/users/?order=**{order}**

### Parameters

| Name  | Parameter type | Type   | Format               | Description                                                                                                    |
|:------|:---------------|:-------|:---------------------|:---------------------------------------------------------------------------------------------------------------|
| order | query          | string | Comma-separated list | A comma-separated list of properties to order the results by. <br>Prefix property with - for descending order. |

### Example request

```http
GET: /api/management/security/users
```

### Response message

| HTTP status code | Reason              | Response model                          |
|:-----------------|:--------------------|:----------------------------------------|
| 200              | Success             | [Pagedlist&lt;User&gt;](/model/user.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)        |
| 404              | NotFound            | [Error](/key-concepts/errors.md)        |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)        |

---