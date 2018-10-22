---
description: Entries can be unpublished using the following workflow event invocation.
---
# Unpublishing entries

Unpublishing an entry stops the entry from being returned in the Delivery API, removing it from your website.

An entry can be unpublished by invoking the sysUnpublish workflow event.

## Unpublish a single entry variation

A single entry language variation can be unpublished by specifying the language.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/workflow/events

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| entryId   | path | string |  | The entry identifier |
| trigger | body | object | [WorkflowTrigger](/model/workflow-trigger.md) | Details to invoke the workflow event |

### Example

```json
POST: /api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c/workflow/events

{
    "language": "en-GB",
    "event": "sysUnpublish"
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | BadRequest | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | Conflict | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

## Unpublish all entry variations

All entry language variations can be unpublished, this is done in the same way as unpublishing a single entry language variation, however in this case the language is omitted.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/workflow/events

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| entryId   | path | string |  | The entry identifier |
| trigger | body | object | [WorkflowTrigger](/model/workflow-trigger.md) | Details to invoke the workflow event |

### Example

```json
POST: /api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c/workflow/events
{
    "event": "sysUnpublish"
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Entry](/model/entry.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | BadRequest | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | Conflict | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |