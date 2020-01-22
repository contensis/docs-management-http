---
description: Marking a block version as broken ensures that it cannot be released to be used in production.
---
# Mark a block version as broken

Marking a block version as broken ensures that it cannot be [released](/blocks/release-a-block-version.md) to be used in production. If a released version that is currently live is marked as broken, then it is [rolled back](/blocks/rollback-a-block-version.md). 

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/actions

## Properties

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|----------------|--------|--------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |


## Remarks

## Example

```json
Accept: application/json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "markAsBroken",
    "data": {
        "version": "2.0"
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