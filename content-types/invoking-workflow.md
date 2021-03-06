---
description: Workflow events can be invoked using the following POST request.
---
# Invoking workflow

Workflow events can be invoked using the following POST request.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/workflow/events

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| contentTypeId   | path | string |  | The content type identifier |
| trigger | body | object | [WorkflowTrigger](/model/workflow-trigger.md) | Details to invoke the workflow event |

## Example

POST: /api/management/projects/movieDb/contenttypes/blog/workflow/events

```json
{
    "language": "en-GB",
    "version": "2.0",
    "event": "publish"
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Entry](/model/content-type.md)         |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | BadRequest          | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |