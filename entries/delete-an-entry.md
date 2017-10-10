## Delete an entry

Deletes an entry by its Id.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |
| entryId | path | string | GUID | The entry identifier. |

### Example request

```http
Accept: application/json
DELETE: /api/management/projects/movieDb/entries/movie/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |