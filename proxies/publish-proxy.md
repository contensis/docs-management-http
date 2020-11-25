---
description: Proxies can be published using the following workflow POST request.
---
# Invoking workflow - Publish

Proxies can be published using the following workflow POST request.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/proxies/**{proxyId}**/workflow/events

## Parameters

| Name      | Parameter type | Type   | Format                                        | Description                                                                                            |
|:----------|:---------------|:-------|:----------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| projectId | path           | string |                                               | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| proxyId   | path           | string |                                               | The proxy identifier                                                                                   |
| trigger   | body           | object | [WorkflowTrigger](/model/workflow-trigger.md) | Details to invoke the workflow event                                                                   |

## Example

POST: /api/management/projects/movieDb/proxies/b65bf285-d66f-48f7-9130-7f8e166f9f62/workflow/events

```json
{
    "version": "1.2",
    "event": "publish"
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Proxy](/model/proxy.md)         |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | BadRequest          | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |