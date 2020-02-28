---
description: Deletes a renderer resource.
---
## Delete a renderer

Deletes a renderer resource.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/renderers/**{rendererId}**

## Parameters

| Name       | Parameter type | Type   | Format | Description                                                                                            |
|------------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId  | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| rendererId | path           | string |        | The renderer identifier                                                                                |

### Remarks

### Example request

```json
DELETE: /api/management/projects/website/renderers/newsRecord
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 204              | No content            |                                  |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | NotFound              | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |