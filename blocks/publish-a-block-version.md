---
description: Publishing a released block version is an action that makes the specified block version live.
---
# Publish a block version

Publishing a released block version is an action that makes the specified block version live. The block version gets a [Deployment status](/blocks/blockversion-statuses.md#deployment-status) of *live* and the previous live version is updated to have a [Deployment status](/blocks/blockversion-statuses.md#deployment-status) of *deprecated*. 

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/actions

## Properties

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|----------------|--------|--------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |


## Remarks

If the specified version is either not a released version or marked as broken, then a validation error is returned.

## Example

```json
Accept: application/json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "makeLive",
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