---
description: Moves a node.
---
# Move a node

Moves a node.

This is a special case of [updating a node.](update-a-node.md) By changing the parent id of a node and updating the node and all of its children will be moved so that they are now descendants of the parent node, with the same hierarchical structure.

<span class="label label--post">PUT</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**

| Name | Parameter type | Type | Format | Description |
| :- | :- | :- | :- | :- |
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| nodeId | path | string | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The identifier of the node to update |
| node | body | object | [Node](/model/node.md) | The node object to update |

### Example request

```json
PUT: /api/management/projects/website/nodes/d6bdea41-729c-4a07-85bf-a392aa0afc2b

{
    // Change the parent id to move the node
    "parentId": "f3322e4f-72b5-4064-be88-fcfed6c82635",
    "title": {
        "en-GB": "Tiger Escaped From Zoo"
    },
    "slug": {
        "en-GB": "tiger-escaped-from-zoo"
    },
    "entryId": "9272ac06-1b3a-4e68-ac1b-a05828b0f7d6"
}
```

### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | OK | [Node](/model/node.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
