---
description: 
---
# Get a block version

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/**{branchId}**/versions/{version}

## Parameters

| Name          | Parameter type | Type   | Format                  | Description                                                                                            |
| :--------     | :------------- | :----- | :---------------------- | :----------------------------------------------------------------------------------------------------- |
| projectId     | path           | string |                         | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| blockId       | path           | string |                         | The block identifier                                                                                   |
| branchId      | path           | string |                         | The branch identifier                                                                                  |
| version       | path           | string | 'latest' or VersionNo   | The version number of a block version, or 'latest'                                                     |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/blocks/movie-listing/master/versions/2.0
```

### Response message

| HTTP status code | Reason              | Response model                            |
| :--------------- | :------------------ | :---------------------------------------- |
| 200              | Success             | [Block version](/model/block-version.md)  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |

### Validations