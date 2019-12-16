---
description: Deletes a component from a specific project.
---

# Delete a component

Deletes a component from a specific project.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/components/**{componentId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string | | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| componentId | path | string | | The component identifier. |

## Example request

```http
DELETE: /api/management/projects/movieDb/components/movieRole
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             |                                  |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

## Validations

### Deleting a component which is in use

If a component is in use within a content type then it can't be deleted. If you attempt to delete a component which is in use you will get the following response.

```json
{
    "logId": "6eda131e-c8eb-44dc-8665-ae3a8b1815d8",
    "message": "There are validation errors deleting the component",
    "data": [
        {
            "field": "",
            "message": "The component cannot be deleted as it is in use in one or more content types"
        }
    ],
    "type": "Validation"
}
```
