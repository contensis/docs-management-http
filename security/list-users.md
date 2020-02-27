---
description: User resources can be retrieved as a paged list
---

## List users

User resources can be retrieved as a paged list and ordered by either username

<span class="label label--get">GET</span> /api/management/security/users/?order=**{order}**&q=**{q}**&pageIndex=**{pageIndex}**&pageSize=**{pageSize}**

### Parameters

| Name      | Parameter type | Type   | Format               | Description                                                                                                    |
|:----------|:---------------|:-------|:---------------------|:---------------------------------------------------------------------------------------------------------------|
| pageIndex | query          | number | integer              | The index of the page.                                                                                          |
| pageSize  | query          | number | integer              | The number of results per page. The default is 25.                                                             |
| q         | query          | string |                      | A simple query to perform a 'contains' search over users firstname, surname, username and email.               |
| order     | query          | string | Comma-separated list | A comma-separated list of properties to order the results by. <br>Prefix property with - for descending order. |

### Example request

```http
GET: /api/management/security/users?q=tyler&pageSize=5
```

### Response message

| HTTP status code | Reason              | Response model                          |
|:-----------------|:--------------------|:----------------------------------------|
| 200              | Success             | [Pagedlist&lt;User&gt;](/model/user.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)        |
| 404              | NotFound            | [Error](/key-concepts/errors.md)        |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)        |

---