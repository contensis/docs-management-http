---
description: Workflow events can be invoked using the following POST request.
---
# Invoking workflow

Workflow events can be invoked using the following POST request.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/workflow/events

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| entryId   | path | string |  | The entry identifier |
| trigger | body | object | [WorkflowTrigger](/model/workflow-trigger.md) | Details to invoke the workflow event |

## Example

POST: /api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c/workflow/events

```json
{
    "language": "en-GB",
    "version": "2.3",
    "event": "draft.submit",
    "data": {
        "message": "Have updated the final paragrah"
    }
}
```

## Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | BadRequest | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
