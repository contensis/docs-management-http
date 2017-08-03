# Components

## Get a component

Gets an existing component by the component id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/components/**{componentId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| componentId | path | string |  | The component identifier |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest* |
| version | query | string | [versionNo](/model/version.md#versionNo)  | The specific version requested |

### Example request

```http
GET: /api/management/projects/movieDb/components/movieRole/
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Component](/model/content-type.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Remarks

If a specific *versionNo* value has been provided then the *versionStatus* value will be ignored.


## Create a component

Creates a new component resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/components/

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |

### Example request

```http
POST: /api/management/projects/movieDb/components/

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
    "dataFormat": "component",
    "version": {
        "createdBy": "s.derrickson",
        "created": "2016-10-12T09:29:18.5144641+01:00",
        "modifiedBy": "b.cumberbatch",
        "modified": "2016-10-13T10:15:12.1973648+01:00",
        "publishedBy": "b.cumberbatch",
        "published": "2016-10-13T10:15:12.1973648+01:00",
        "versionNo": "0.2"
    }
}
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | [Content Type](/model/content-type.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | Conflict | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
**TODO: Add validation responses**

### Validations

| Type | Description |
|-|-|
| Project does not exist | A project must exist to be able to create components |
| Non-unique id | The content type or component must be unique for the project |

### Remarks

## Update a component
Updates an existing component resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/components/**{componentId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| componentId | path | string |  | The component identifier |

### Example request

```http
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

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Updated | [Component](/model/component.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 409 | NotLatestVersion | [Error](/key-concepts/errors.md) |
| 422 | ValidationError | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |


## Publish a component

Publishes a component making it available for use in content types.

<span class="label label--get">PUT</span> /api/management/workflow

## Parameters

None.

### Example request

```http
PUT: /api/management/workflow

{  
   "projectId":"website",
   "id":"movieRole",
   "objectVersion":"0.1",
   "type":"Component",
   "workflowName":"ContensisDefault",
   "events":[  
      "Submit",
      "Approve"
   ]
}

```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Component [...]](/model/component.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 403 | BadRequest | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |


# See also
[Add a component to a content type](/key-concepts/content-types.md#add-a-component-to-a-content-type)


## Delete a component

Deletes a component from a specific project.

<span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/components/**{componentId}**

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier |
| componentId | path | string |  | The component identifier |

### Example request

```http
DELETE: /api/management/projects/movieDb/components/movieRole
```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success |  |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |
