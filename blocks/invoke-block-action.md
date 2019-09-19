---
description: 
---
# Invoke a block action


<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/blocks/movie-listing/actions

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
| :-------- | :------------- | :----- | :----- | :----------------------------------------------------------------------------------------------------- |
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

### Rollback a block version

```json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "rollback",
}
```

### Release a block version

```json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "release"
}
```

### Mark a block version as broken

```json
POST: /api/management/projects/movieDb/blocks/movie-listing/actions
{
    "type": "markAsBroken",
    "data": {
        "version": "1.0"
    }
}
```

### Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 202              | Accepted            |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations