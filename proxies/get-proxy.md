---
description: Gets an existing proxy resource.
---
## Get a proxy

Gets an existing proxy resource.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/proxies/**{proxyId}**

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
|-----------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| proxyId   | path           | string | GUID   | The proxy identifier                                                                                   |

### Remarks

### Example request

```http
GET: /api/management/projects/website/proxies/ec0b25dc-0c46-4a90-8610-c0886c51b709
```

### Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | OK                  | [Proxy](/model/proxy.md)         |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |