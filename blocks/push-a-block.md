---
description: Pushing a block resource will either create the first block and block version resources or will create a new block version with an incremented version number that has a matching id.
---
# Push a block

Pushing a block resource will either create the first block and block version resources or will create a new block version with an incremented version number that has a matching id. A pushed block includes the source control details for the last commit, including the branch name and commit id, to help identify the change set for the block version. The location and tag for the docker image are also required for discovery and hosting.

Pushing a new block version automatically sets the [Deployment status](/blocks/block-statuses.md#deployment-status) as *Deployed* and updates the previous minor version's [Deployment status](/blocks/block-statuses.md#deployment-status) as *Deprecated*.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|----------------|--------|--------|--------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

## Remarks

The resource used to push a block is a subset of the final [block version](/model/block-version.md) as the remaining properties (i.e. endpoints, static paths, etc) are automatically 'discovered' by the publishing platform by inspecting the referenced docker image and extracting the details defined in the manifest file. 

### Example request

```http
Accept: application/json
POST: /api/management/projects/movieDb/blocks/
{
    "id": "movieListing",
    "projectId": "movieDb",
    "image": {
        "uri": "moviedb/movie-listing",
        "tag": "81e13d08"
    },
    "source": {
        "branch": "master",
        "commit": {
            "id": "81e13d08",
            "message": "Implemented movie listing",
            "uri": "https://github.com/moviedb/movie-listing/commit/81e13d08fb8fd33e37b64b1e95e1668e5256b38b",
        }        
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