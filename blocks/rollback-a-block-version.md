---
description: Rolling back a live block version removes it from production use and automatically replaces it with the previously released major version.
---
# Rollback a block version

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/actions

Rolling back a live block version removes it from production use and automatically replaces it with the previously released major version. This is useful when a recently published block version is not behaving correctly and you want to revert the change quickly. 

## Properties

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|----------------|--------|--------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |


## Remarks

Only actively live versions of a block can be rolled back.

## Example

```http
Accept: application/json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "rollback",
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
| 404              | NotFound            | [Error](/key-concepts/errors.md)         |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)         |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)         |