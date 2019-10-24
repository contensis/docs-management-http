---
description: Gets a specific block version by label or version number.
---
# Get a block version

Gets a specific block version by label or version number.

A label of *live* will request the version that is currently the live production version. A label of *latest* will return the last pushed version of the block.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/**{branchId}**/versions/**{version}**

## Parameters

| Name      | Parameter type | Type   | Format                  | Description                                                                                            |
|-----------|----------------|--------|-------------------------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |                         | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| blockId   | path           | string |                         | The block identifier                                                                                   |
| branchId  | path           | string |                         | The branch identifier                                                                                  |
| version   | path           | string | label or version number | A label of either *live* or *latest*, or a valid two-part version number, e.g. 1.7                     |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/blocks/movielisting/master/versions/2.0
```

### Response message

| HTTP status code | Reason              | Response model                           |
|------------------|---------------------|------------------------------------------|
| 200              | Success             | [Block version](/model/block-version.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)         |
| 404              | NotFound            | [Error](/key-concepts/errors.md)         |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)         |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)         |