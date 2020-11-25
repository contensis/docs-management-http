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
    "id": "7622b5f7-e245-4226-9e64-3aeafa930eae",
    "projectId": "movieDb",
    "name": "Thrillers section",
    "description": "Proxies current website thrillers section",
    "endpoints": {
        "*": {
            "server": "10.65.18.4",
            "ssl": true,
            "headers": {
                "host": "www.moviedb-oldsite.com"
            }
        },
        "fr-FR": {
            "server": "10.65.18.4",
            "ssl": true,
            "headers": {
                "host": "www.moviedb.fr"
            }
        }
    },
    "version": {
        "versionNo": "2.0",
        "created": "2020-02-13T10:15:12.1973648+01:00",
        "createdBy": "t.durden",
        "modified": "2020-02-13T10:15:12.1973648+01:00",
        "modifiedBy": "t.durden",
        "published": "2020-02-13T10:15:12.1973648+01:00",
        "publishedBy": "t.durden"
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