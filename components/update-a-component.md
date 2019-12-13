---
description: Updates an existing component resource.
---

# Update a component

Updates an existing component resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/components/**{componentId}**

## Parameters

| Name        | Parameter type | Type   | Format | Description                                                                                             |
|:------------|:---------------|:-------|:-------|:--------------------------------------------------------------------------------------------------------|
| projectId   | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| componentId | path           | string |        | The component identifier.                                                                               |

## Example request

```json
PUT: /api/management/projects/movieDb/components/movieRole

{
  "id": "movieRole",
  "projectId": "website",
  "name": {
    "en-GB": "Movie Role"
  },
  "description": {
    "en-GB": "A Persons role within a movie"
  },
  "fields": [
    {
        "id": "person",
        "name": {
            "en-GB": "Person"
        },
        "dataType": "object",
        "dataFormat": "entry",
        "description": {
            "en-GB": "The actor or crew member"
        },
        "default": {},
        "validations": {
            "allowedContentTypes": {
                "contentTypes": ["person"]
            }
        },
        "editor": {
            "id": "entry",
            "instructions": {
                "en-GB": ""
            },
            "properties": {
                "placeholderText": {
                    "en-GB": ""
                }
            }
        }
    },
    {
      "id": "role",
      "name": {
        "en-GB": "Role"
      },
      "dataType": "String",
      "dataFormat": null,
      "description": {},
      "default": {},
      "validations": null,
      "editor": null
    }  
  ],
  "workflowId": "ContensisDefault",
  "dataFormat": "component"
}
```

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Updated             | [Component](/model/component.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 409              | NotLatestVersion    | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
