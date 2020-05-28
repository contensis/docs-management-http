---
description: Deletes a workflow definition within a specific project.
---

## Delete a workflow definition

Deletes a workflow definition within a specific project.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| workflowDefinitionId | path | string |  | The workflow definition identifier. |

### Example request

```http
DELETE: /api/management/projects/movieDb/workflow/definitions/approvalWorkflow
```

### Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | Success             |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
