---
description: Get root node.
---
# Get the root node

Gets the root node of the specified project.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/root

| Name | Parameter type | Type | Format | Description |
| :- | :- | :- | :- | :- |
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

## Example request

```http
GET: /api/management/projects/website/nodes/root
```

## Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Node](/model/node.md)           |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |