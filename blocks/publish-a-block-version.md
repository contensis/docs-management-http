---
description: .
---
# Release a block version

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/actions




## Properties

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|----------------|--------|--------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |


## Remarks

## Example

```http
Accept: application/json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "makeLive",
    "data": {
        "version": "1.5"
    }
}
```

### Response message

| HTTP status code | Reason              | Response model                           |
|------------------|---------------------|------------------------------------------|
| 202              | Accepted            | [Block version](/model/block-version.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)         |
| 404              | ProjectNotFound     | [Error](/key-concepts/errors.md)         |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)         |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)         |