---
description: Get a block by ID for a project.
---
# Get a block

Get a block by it's id for a project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| blockId   | path           | string |        | The identifier, e.g news                                                                               |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/blocks/movie-listing
```

### Response message

| HTTP status code | Reason              | Response model                   |
|------------------|---------------------|----------------------------------|
| 200              | Success             | [Block](/model/block.md)         |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |