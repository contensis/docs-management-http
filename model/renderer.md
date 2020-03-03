---
description: TODO
---
# Renderer

TODO:

## Properties

### Renderer

| Name                 | Type        | Format               | Description                              |
|----------------------|-------------|----------------------|------------------------------------------|
| id                   | string      |                      | The renderer api identifier              |
| name                 | string      |                      | The renderer friendly name               |
| description          | string      |                      | An optional description for the renderer |
| assignedContentTypes | string[...] |                      | An optional description for the renderer |
| rules                | object[...] | rule                 | An optional description for the renderer |
| version              | object      | [version](./version) | An optional description for the renderer |

### Rule

| Name   | Type   | Format | Description                                         |
|--------|--------|--------|-----------------------------------------------------|
| return | object |        | The default result from the renderer rule execution |

## Example

```json
{
    "id": "newsRecord",
    "name": "News record",
    "description": "Renders news record entries",
    "assignedContentTypes": [
        "newsRecord"
    ],
    "rules": [
        {
            "return": {
                "blockId": "news",
                "endpointId": "news-record"
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