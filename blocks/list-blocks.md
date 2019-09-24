---
description: 
---
# List blocks
<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks

## Parameters

| Name             | Parameter type | Type    | Format                                            | Description                                                                                            |
| :--------        | :------------- | :------ | :------------------------------------------------ | :----------------------------------------------------------------------------------------------------- |
| projectId        | path           | string  |                                                   | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/blocks
```

### Response message

| HTTP status code | Reason              | Response model                            |
| :--------------- | :------------------ | :---------------------------------------- |
| 200              | Success             | [PagedList&lt;Block&gt;](/model/block.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |