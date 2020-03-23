---
description: Updates an existing proxy resource.
---
## Update a proxy

Updates an existing proxy resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/proxies/**{proxyId}**

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| proxyId   | path           | string | GUID   | The proxy identifier                                                                                   |

### Remarks

Proxy resources follow the standard optimistic concurrency model and so the versionNo field is required for an update.

### Example request

```http
PUT: /api/management/projects/movieDb/proxies/ec0b25dc-0c46-4a90-8610-c0886c51b709

{
    "id": "ec0b25dc-0c46-4a90-8610-c0886c51b709",
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
    },
    "version": {
        "versionNo": "1.3",
    }
}
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 200              | OK                    | [Proxy](/model/proxy.md)         |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | NotFound              | [Error](/key-concepts/errors.md) |
| 422              | ValidationError       | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |