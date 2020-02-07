---
description: Group resources can be retrieved as a paged list
---

## List groups

Group resources can be retrieved as a paged list.

<span class="label label--get">GET</span> /api/management/security/groups/?order=**{order}**&q=**{q}**&pageIndex=**{pageIndex}**&pageSize=**{pageSize}**

### Parameters

| Name      | Parameter type | Type   | Format               | Description                                                                                                       |
|:----------|:---------------|:-------|:---------------------|:------------------------------------------------------------------------------------------------------------------|
| pageIndex | query          | number | integer              | The index of the page.                                                                                            |
| pageSize  | query          | number | integer              | The number of results per page. The default is 25.                                                                |
| q         | query          | string |                      | A simple case-insensitive query to perform a 'contains' search over group names. |
| order     | query          | string | Comma-separated list | A comma-separated list of properties to order the results by. <br>Prefix property with - for descending order.    |

### Example request

```http
GET: /api/management/security/groups?q=mayhem
```

### Response message

| HTTP status code | Reason              | Response model                          |
|:-----------------|:--------------------|:----------------------------------------|
| 200              | Success             | [Pagedlist&lt;Group&gt;](/model/group.md) |
| 403              | Forbidden           | [Error](/key-concepts/errors.md)        |
| 404              | NotFound            | [Error](/key-concepts/errors.md)        |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)        |