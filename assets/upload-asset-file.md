---
description: Asset files are uploaded before an asset can be created.
---
## Upload asset file

A file is required to be uploaded to the asset resource endpoint before an asset can be created. A content type of multipart/form-data is used to perform the upload. A file id is returned for a successful upload which then can be used as a file reference in a [AssetFile](/model/assetfile.md) field when creating an asset. Multiple files can be uploaded in a single request with the resulting file ids returning in the same order as they are uploaded.  

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/assets/

### Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier. |

### Example request

```http
POST /api/management/projects/website/assets HTTP/1.1
Authorization: Bearer [YOUR_AUTH_TOKEN]
Content-Type: multipart/form-data;
Content-Length: 230563
boundary=--upload_boundary

--upload_boundary
Content-Type: image/jpeg

[JPEG_DATA]

--upload_boundary
Content-Type: image/jpeg

[JPEG_DATA]
--upload_boundary--


```

### Response message

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 201 | Created | Array of file id objects |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |

### Example

```json
[
    {
        "fileId": "25bd73bb-cbb0-454f-a762-2bee08a68cbe.jpg"
    },
    {
        "fileId": "97d70ad2-017f-46ff-8d9e-f8d054652d9c.jpg"
    }
]
```