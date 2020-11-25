---
description: Lists proxy resources for a project.
---
## List proxies

Lists proxy resources for a project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/proxies/

## Parameters

| Name          | Parameter type | Type   | Format | Description                                                                                            |
|---------------|:---------------|:-------|:-------|:-------------------------------------------------------------------------------------------------------|
| projectId     | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| versionStatus | query          | string |        | The version status, either published or latest. The default is latest.                                 |


### Example request

```http
GET: /api/management/projects/website/proxies/
```

### Response messages

| HTTP status code | Reason              | Response model                            |
|:-----------------|:--------------------|:------------------------------------------|
| 200              | OK                  | PagedList&lt;[Proxy](/model/proxy.md)&gt; |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |