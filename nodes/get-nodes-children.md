---
description: Gets the node's children.
---
# Get node's children

Gets the children of a specific node.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/**{parentNodeId}**/children

## Parameters

| Name | Parameter type | Type | Format | Description |
| :- | :- | :- | :- | :- |
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| parentNodeId | query | string | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The id of the parent node for the child nodes that will be returned |

## Example request

```http
GET: /api/management/projects/website/nodes/f3322e4f-72b5-4064-be88-fcfed6c82635/children
```

## Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Node [...]](/model/node.md)     |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
