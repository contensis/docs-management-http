---
description: Releasing a block version is an action that marks the block version as being ready for production use.
---
# Release a block version

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/actions

Releasing a block version is an action that marks the block version as being ready for production use. This is a workflow action typically performed by the developer(s) producing the block. Releasing a block version moves it's [workflow status](/blocks/block-statuses#workflow-status.md) from *Draft* to *Released* and sets the version number to a major release. Once a block version is released then it can be selected to be used within a Renderer for use within a live website. 


## Properties

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|----------------|--------|--------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |


## Remarks

If the version specified is not the latest version or the version is already a released version, then a validation error will be returned.

## Example

```http
Accept: application/json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "release",
    "data": {
        "version": "0.9"
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