---
description: Workflow events can be invoked for a workflow definition using the following POST request.
---
# Invoking workflow for a workflow definition

Workflow events can be invoked for a workflow definition using the following POST request.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}**/workflow/events

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| workflowDefinitionId | path | string |  | The workflow definition identifier. |
| trigger | body | object | [WorkflowTrigger](/model/workflow-trigger.md) | Details to invoke the workflow event |

## Example

POST: /api/management/projects/movieDb/workflow/definitions/approvalWorkflow/workflow/events

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
| 200              | Success             | [Workflow Definition](/model/workflow-definition.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 403              | BadRequest          | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 409              | NotLatestVersion            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |


## Validations

| Type | Description |
|-|-|
| Project does not exist | A project must exist to be able to publish a workflow definition. |
| Id missing | The workflow definition id must be defined. |
| Workflow definition not found | The workflow definition must exist in order to be deleted. |
| Version not latest | Only the latest version of a workflow definition can be published. |
| Workflow definition already published | The latest version of the workflow definition has already been published. |
