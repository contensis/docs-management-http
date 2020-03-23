---
description: 
---
# Block version

A block version represents an incrementally pushed instance of a block. 

## Properties

| Name                   | Type     | Format                                                           | Description                                                         |
|:-----------------------|:---------|:-----------------------------------------------------------------|:--------------------------------------------------------------------|
| id                     | string   |                                                                  | The block identifier as a camel-cased unique string                 |
| projectId              | string   |                                                                  | The project identifier, e.g. website                                |
| status.broken          | boolean  |                                                                  | Whether the block has been marked as broken                         |
| status.deployment      | string   | [Deployment status](/blocks/blockversion-statuses.md#deployment-status) | The block version deployment status                                 |
| status.running         | string   | [Running status](/blocks/blockversion-statuses.md#running-status)       | The block version running status                                    |
| status.workflow        | string   | [Workflow status](/blocks/blockversion-statuses.md#workflow-status)     | The block version workflow status                                   |
| endpoints              | object[] |                                                                  | The endpoints exposed by this block version                         |
| endpoints[].id         | string   |                                                                  | The endpoint identifier                                             |
| endpoints[].path       | string   | URI path                                                         | The path to the invocable endpoint                                  |
| endpoints[].type       | string   | *pagelet* or *layout*                                            | The type of endpoint, either *pagelet* or *layout*                  |
| staticPaths            | string[] |                                                                  | The static path root                                                |
| image                  | object   |                                                                  | The docker image repository details                                 |
| image.uri              | string   |                                                                  | The image repository uri                                            |
| image.tag              | string   |                                                                  | The image tag name                                                  |
| source                 | object   |                                                                  | The source control commit details                                   |
| source.branch          | string   |                                                                  | The source control branch name                                      |
| source.commit.id       | string   |                                                                  | The source control commit identifier                                |
| source.commit.message  | string   |                                                                  | The source control commit message                                   |
| source.commit.uri      | string   |                                                                  | The source control commit uri                                       |
| version                | object   |                                                                  | The block version version info                                      |
| version.pushedBy       | string   |                                                                  | The username of the person who pushed the block version             |
| version.pushed         | object   | datetime                                                         | The date/time of the pushed action                                  |
| version.releasedBy     | object   |                                                                  | The username of the person who released the block version           |
| version.released       | object   | datetime                                                         | The date/time of the release action                                 |
| version.markedBrokenBy | object   |                                                                  | The username of the person who declared the block version as broken |
| version.markedBroken   | object   | datetime                                                         | The date/time of the marked as broken action                        |
| version.madeLiveBy     | object   |                                                                  | The username of the person who made the block live                  |
| version.madeLive       | object   | datetime                                                         | The date/time of the make block live action                         |

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
            "uri": "https://gitlab.zengenti.com/container-examples/razor-pages/commit/81e13d08fb8fd33e37b64b1e95e1668e5256b38b"
        }        
    },
    "version": {
        "pushedBy": "s.derrickson",
        "pushed": "2016-10-12T09:29:18.5144641+01:00",
        "releasedBy": "b.cumberbatch",
        "released": "2016-10-13T10:15:12.1973648+01:00",
        "markedBrokenBy": null,
        "markedBroken": null,
        "madeLiveBy": null,
        "madeLive": null,
        "versionNo": "2.0"
    }
}
```