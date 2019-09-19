---
description: 
---
# Get a block


<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**

## Parameters

| Name          | Parameter type | Type   | Format                                    | Description                                                                                            |
| :--------     | :------------- | :----- | :-----------------------------------------| :----------------------------------------------------------------------------------------------------- |
| projectId     | path           | string |                                           | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| versionStatus | query          | string |                                           | The version status of the block. "latest" or "deployed"                                                |
| version       | query          | string | [versionNo](/model/version.md#versionNo)  | The specific version requested.                                                                        |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/blocks/movie-listing
```

### Response message

| HTTP status code | Reason              | Response model                            |
| :--------------- | :------------------ | :---------------------------------------- |
| 200              | Success             | [Block](/model/block.md)                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |

### Validations