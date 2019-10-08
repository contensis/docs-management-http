---
description: Creates a new node.
---
# Create a node

Creates a new child node under a specified parent node .

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/nodes/**{parentNodeId}**/children

## Parameters

| Name | Parameter type | Type | Format | Description |
| :- | :- | :- | :- | :- |
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| parentNodeId | path | string | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The parent node identifier which the new node will be created as a child |
| node | body | object | [Node](/model/node.md) | The node object to created |

## Example request

```json
POST: /api/management/projects/website/nodes/f3322e4f-72b5-4064-be88-fcfed6c82635/children

{
    "id": "d6bdea41-729c-4a07-85bf-a392aa0afc2b",
    "parentId": "f3322e4f-72b5-4064-be88-fcfed6c82635",
    "displayName": {
        "en-GB": "Tiger Escaped From Zoo",
        "fr-FR": "Tigre échappé du zoo"
    },
    "slug": {
        "en-GB": "tiger-escaped-from-zoo",
    "fr-FR": "tigre-s-est-echappe-du-zoo"
    },
    "restrictedToLanguages": [
        "en-GB",
        "fr-FR"
    ],
    "entryId": "9272ac06-1b3a-4e68-ac1b-a05828b0f7d6"
}
```

## Minimum request

A node can be created by posting only the title:

```json
POST: /api/management/projects/website/nodes/f3322e4f-72b5-4064-be88-fcfed6c82635/children

{
    "parentId": "f3322e4f-72b5-4064-be88-fcfed6c82635",
    "displayName": {
        "en-GB": "Tiger Escaped From Zoo"
    }
}
```

## Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 201              | Created               | [Node](/model/node.md)           |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | NotFound              | [Error](/key-concepts/errors.md) |
| 409              | ResourceAlreadyExists | [Error](/key-concepts/errors.md) |
| 422              | ValidationError       | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |

## Validations

### Parent id

A node must have a parent id. If you attempt to create a node without a parent id you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "The parent id cannot be an empty guid"
        }
    ],
    "type": "Validation"
}
```

### Parent child limit

A parent node cannot have more than 2000 children. If you attempt to create a node which breaches this limit you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "A parent must not have more than 2000 children"
        }
    ],
    "type": "Validation"
}
```

### Depth limit

The maximum depth of a node is 10 levels. If you attempt to create a node which breaches this limit you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "The maximum depth for a node is 10 levels deep"
        }
    ],
    "type": "Validation"
}
```

### Slug

A node must have at least one slug for a language. If you attempt to create a node without a slug you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "A slug is required for at least one language"
        }
    ],
    "type": "Validation"
}
```

A node slug cannot be longer than 50 characters. If you attempt to create a node with a slug which breaches this you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "The node slug cannot be longer than 50 characters"
        }
    ],
    "type": "Validation"
}
```

A node slug must be unique for a language on a given parent node. If you attempt to create a node which breaks this rule you will get the following response:

```json
{
    "logId": "00000000-0000-0000-0000-000000000000",
    "message": "There were validation errors creating the node",
    "data": [
        {
            "field": "",
            "message": "The node slug repeatedSlug exists for the language en-GB in parent f3322e4f-72b5-4064-be88-fcfed6c82635 in the tree 1126b642-409b-4372-bb17-0bdb7f641a5d"
        }
    ],
    "type": "Validation"
}
```

