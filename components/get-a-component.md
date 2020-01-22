---
description: A component determines a reusable schema added to content types which entries are then created from.
---
# Components

A component determines a reusable schema added to content types which entries are then created from. Components contain a list of fields just like content types, and allow for a standardized schema for modelling content.[Find out more about components on ZenHub](https://zenhub.zengenti.com/Contensis/12.0/kb/content-types-and-entries/components/components-overview.aspx)

## Get a component

Gets an existing component by the component Id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/components/**{componentId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| componentId | path | string |  | The component identifier. |
| versionStatus | query | string |  | The version status, either *published* or *latest*. The default is *latest*. |
| version | query | string | {Major}.{Minor} | The version number of the resource. |

### Example request

```http
GET: /api/management/projects/movieDb/components/movieRole/
```

### Response message

| HTTP status code | Reason              | Response model                      |
|:-----------------|:--------------------|:------------------------------------|
| 200              | Success             | [Component](/model/component.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)    |
| 404              | NotFound            | [Error](/key-concepts/errors.md)    |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)    |

### Remarks

If a specific *versionNo* value has been provided then the *versionStatus* value will be ignored.
