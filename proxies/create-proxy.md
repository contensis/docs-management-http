---
description: Creates a new proxy resource.
---
## Create a proxy

Creates a new proxy resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/proxies

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

### Remarks

### Example request

```http
POST: /api/management/projects/website/proxies

{
    "projectId": "movieDb",
    "name": "Thrillers section",
    "description": "Proxies current website thrillers section",
    "endpoints": {
        "*": {
            "uri": "https://10.32.187.17:443/movies/thrillers",
            "headers": {
                "host": "www.moviedb.com",
            }
        }
    }
}
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 201              | Created               | [Proxy](/model/proxy.md)         |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | NotFound              | [Error](/key-concepts/errors.md) |
| 409              | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422              | ValidationError       | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |