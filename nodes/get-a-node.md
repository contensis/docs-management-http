---
description: Get a node.
---
# Get a node

Get a node by ID.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**/

## Parameters

| Name | Parameter type | Type | Format | Description |
| :- | :- | :- | :- | :- |
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| nodeId | query | string | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The id of the node to retrieve |

## Example request

```http
GET: /api/management/projects/website/nodes/d6bdea41-729c-4a07-85bf-a392aa0afc2b
```

## Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Node](/model/node.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
