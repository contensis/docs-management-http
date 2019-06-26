---
description: Deletes a node.
---
# Delete a node

Deletes a node by ID.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**/

## Parameters

| Name | Parameter type | Type | Format | Description |
| :- | :- | :- | :- | :-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| nodeId | query | string | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The id of the node to delete |

## Example request

```http
DELETE: /api/management/projects/website/nodes/d6bdea41-729c-4a07-85bf-a392aa0afc2b
```

## Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 204 | Success | No content |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
