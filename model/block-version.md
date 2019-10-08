---
description: .
---
# Block version

TODO

## Properties

| Name                  | Type     | Format                                            | Description                                 |
|:----------------------|:---------|:--------------------------------------------------|:--------------------------------------------|
| id                    | string   |                                                   | The block identifier, camel-cased           |
| projectId             | string   |                                                   | The project identifier                      |
| staticPaths           | string[] |                                                   | The static path root                        |
| image.uri             | string   |                                                   | The image repository uri                    |
| image.tag             | string   |                                                   | The image tag name                          |
| source.branch         | string   |                                                   | The source control branch name              |
| source.commit.id      | string   |                                                   | The source control commit identifier        |
| source.commit.message | string   |                                                   | The source control commit message           |
| source.commit.uri     | string   |                                                   | The source control commit uri               |
| status.broken         | boolean  |                                                   | Whether the block has been marked as broken |
| status.deployment     | string   | [Deployment status](/blocks/deployment-status.md) | The block deployment status                 |
| status.running        | string   | [Running status](/blocks/running-status.md)       | The block running status                    |
| status.workflow       | string   | [Workflow status](/blocks/workflow-status.md)     | The block workflow status                   |

## Remarks


## Example response

```json
{
    "id": "blogs",
    "projectId": "website",       
    "status": {
        "broken": false, 
        "deployment": "Deployed",      
        "running": "Available",
        "workflow": "Draft",
    },
    "endpoints": [
        {
            "id": "blogRecord",
            "path": "/blogrecord",
            "type": "pagelet"
        },
        {
            "id": "blogListing",
            "path": "/blogs",
            "type": "pagelet"
        },
        {
            "id": "genericTemplate",
            "path": "/generictemplate",
            "type": "layout"
        },
        {
            "id": "miniBlogList",
            "path": "/minibloglist",
            "type": "pagelet"
        }
    ],
    "staticPaths": [
        "static",
        "image-gallery"
    ],
    "image":{
        "uri": "gitlab.zengenti.com:4567/container-examples/razor-pages/master/razor-example",
        "tag": "81e13d08"
    },
    "source": {
        "branch": "master",
        "commit": {
            "id": "81e13d08",
            "message": "Added marquee tag",
            "uri": "https://gitlab.zengenti.com/container-examples/razor-pages/commit/81e13d08fb8fd33e37b64b1e95e1668e5256b38b",
        }        
    },
    "version": {
        "pushedBy": "s.derrickson",
        "pushed": "2016-10-12T09:29:18.5144641+01:00",
        "releasedBy": "b.cumberbatch",
        "released": "2016-10-13T10:15:12.1973648+01:00",
        "markedBrokenBy": "b.cumberbatch",
        "markedBroken": "2016-10-13T10:15:12.1973648+01:00",
        "versionNo": "2.0"
    }
}
```