---
description: .
---
# Block version

TODO

## Properties

| Name                  | Type      | Format | Description                                      |
|:----------------------|:----------|:-------|:-------------------------------------------------|
| id                    | string    |        | The block identifier, camel-cased                |
| projectId             | string    |        | The project identifier                           |
| staticPaths           | string[]  |        | The static path root                             |
| image.uri             | string    |        | The image repository uri                         |
| image.tag             | string    |        | The image tag name                               |
| source.branch         | string    |        | The source control branch name                   |
| source.commit.id      | string    |        | The source control commit identifier             |
| source.commit.message | string    |        | The source control commit message                |
| source.commit.uri     | string    |        | The source control commit uri                    |
| status                | string    |        | The status of the block                          |


## TODO: Does status become versionStatus, which are documented in the table below?


## Block version status

| Name        | Description                                                               |
|:------------|:--------------------------------------------------------------------------| 
| Discovering | The block has been pushed and it's manifest is currently being discovered |
| Superseded  | The block version has been superseded by another                          |
| Broken      | The block version has been marked as broken                               |
| Live        | The block version is live and available for requests                      |

## Remarks


## Example

?version=latest|release|live
?includeEndpoints=true


```json
{
    "id": "blogs",
    "projectId": "website",
    "endpoints":[
        
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
    "sys": {
        "version": {
            "pushedBy": "s.derrickson",
            "pushed": "2016-10-12T09:29:18.5144641+01:00",
            "releasedBy": "b.cumberbatch",
            "released": "2016-10-13T10:15:12.1973648+01:00",
            "markedBrokenBy": "b.cumberbatch",
            "markedBroken": "2016-10-13T10:15:12.1973648+01:00",
            "versionNo": "2.0"
        } 
    },
    "status": "Live"
}
```

## Response

```json
{
    "id": "1ce750c4-6f5c-4e26-b166-7273985c5697",
    "path": "/blogs"

}

```