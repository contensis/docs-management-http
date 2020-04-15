---
description: TODO
---
# Renderer

TODO:

## Properties

### Renderer

| Name                 | Type        | Format               | Description                                                                                    |
|----------------------|-------------|----------------------|------------------------------------------------------------------------------------------------|
| uuid                 | string      | UUID                 | The renderer identifier as a 128 bit GUID.                                                     |
| id                   | string      |                      | The renderer api identifier                                                                    |
| projectId            | string      |                      | The project api identifier                                                                     |
| name                 | string      |                      | The renderer friendly name                                                                     |
| description          | string      |                      | An optional description for the renderer                                                       |
| layoutRendererId     | string      |                      | An reference to the renderer that will wrap the current renderer output with additional markup |
| assignedContentTypes | string[...] |                      | A list of content types that the renderer will handle the renderering of derived entries for   |
| rules                | object[...] | rule                 | The renderer rule conditions                                                                   |
| version              | object      | [version](./version) | The version details for the renderer resource                                                  |

### Rule

| Name   | Type   | Format | Description                                         |
|--------|--------|--------|-----------------------------------------------------|
| return | object |        | The default result from the renderer rule execution |

## Example

```json
{
    "uuid": "7622b5f7-e245-4226-9e64-3aeafa930eae",
    "id": "newsRecord",
    "projectId": "movieDb",
    "name": "News record",
    "description": "Renders news record entries",
    "layoutRendererId": "layout",
    "assignedContentTypes": [
        "newsRecord"
    ],
    "rules": [
        {
            "return": {
                "blockId": "news",
                "endpointId": "news-record",
                "version": "latest"
            }
        }
    ],
    "version": {
        "versionNo": "2.0",
        "created": "2020-02-13T10:15:12.1973648+01:00",
        "createdBy": "t.durden",
        "modified": "2020-02-13T10:15:12.1973648+01:00",
        "modifiedBy": "t.durden",
        "published": "2020-02-13T10:15:12.1973648+01:00",
        "publishedBy": "t.durden"
    }
}
```