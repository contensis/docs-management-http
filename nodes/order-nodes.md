---
description: Set the node order
---

# Node order

## Set the node order

Sets the node order for the children of a specific parent node and optionally for a language.

<span class="label label--put">PUT</span> /api/management/projects/{projectId}/nodes/{parentNodeId}/children/order

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| parentNodeId | path | string |  | The container node for the children which are being ordered. |
| language | query | string |  | [Optional] The target language that the order is being applied. If no language is specified then the default language order is set. |

### Remarks

The default language order is used for other languages if no language specific order is set.

### Example request

The example below is setting the node order specifically for French.

```http
PUT: /api/management/projects/website/nodes/62722a79-4507-4969-b65e-f6c769ce1336/children/order?language=fr-FR
[
    "62722a79-4507-4969-b65e-f6c769ce1336",
    "9caa58f7-20f5-44ba-a493-685c88556644",
    "ba77f063-77c9-4416-af1a-8f5002650da3",
    "58277007-6c36-4d46-bdba-3ebb11809f9f",
    "59808362-5f55-4fa8-863f-7cc98c1dafca",
    "30be3bac-e671-41a3-af3e-e2acdebe39f1",
    "43224e9e-15a2-40fc-a41f-b239253cc6f1",
    "7ce5f200-9d7c-4025-bf5c-e611c1e3e6b4",
    "f30a1a70-1bea-4292-a7f8-7477b7943675",
    "c4c751ab-9e7d-4843-9458-f38a39ddbfab",
    "163129f1-f459-4ca5-a200-216778b487b1"
]
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 204              | No Content            |                                  |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | Project not found     | [Error](/key-concepts/errors.md) |
| 404              | Parent node not found | [Error](/key-concepts/errors.md) |
| 422              | Language invalid      | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |

---

## Remove the node order

Deletes the node order for the children of a specific parent node and optionally for a language.

<span class="label label--delete">DELETE</span> /api/management/projects/{projectId}/nodes/{parentNodeId}/children/order

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| parentNodeId | path | string |  | The container node for the children which have an order. |
| language | query | string |  | [Optional] The target language that the order is applied. If no language is specified then the default language order is deleted. |

### Example request

The example below is deleting the node order specifically for German.

```json
DELETE: /api/management/projects/website/nodes/62722a79-4507-4969-b65e-f6c769ce1336/children/order?language=de
```

### Response messages

| HTTP status code | Reason                | Response model                   |
|:-----------------|:----------------------|:---------------------------------|
| 204              | No Content            |                                  |
| 401              | Unauthorized          | [Error](/key-concepts/errors.md) |
| 404              | Project not found     | [Error](/key-concepts/errors.md) |
| 404              | Parent node not found | [Error](/key-concepts/errors.md) |
| 422              | Language invalid      | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError   | [Error](/key-concepts/errors.md) |