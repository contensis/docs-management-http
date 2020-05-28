---
description: Gets an existing workflow definition by the workflow definition Id.
---
# Workflow definitions

## Get a workflow definition

Gets an existing workflow definition by the workflow definition Id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| workflowDefinitionId | path | string |  | The workflow definition identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |

### Example request

```http
GET: /api/management/projects/movieDb/workflow/definitions/approvalWorkflow/
```

### Response message

| HTTP status code | Reason              | Response model                         |
|:-----------------|:--------------------|:---------------------------------------|
| 200              | Success             | [Workflow Definition](/model/workflow-definition.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 404              | NotFound            | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |
