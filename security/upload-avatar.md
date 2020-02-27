---
description: 
---

# Upload a user avatar

A user image avatar can uploaded by performing a PUT action with a content type of multipart/form-data.

<span class="label label--put">PUT</span> /api/management/security/users/**{userId}**/avatar?**{transformations}**

## Parameters

| Name   | Parameter type | Type   | Format | Description          |
|:-------|:---------------|:-------|:-------|:---------------------|
| userId | path           | string | GUID   | The user identifier. |
|  | path           | string | GUID   | The user identifier. |

## Remarks

Only the current user and a member of the System Administrators group can update a user avatar.

## Example request

```http
POST /api/management/security/users/14d41e59-2418-4bc9-8489-a9eae123a452/avatar HTTP/1.1
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

## Response message

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 204              | No Content          |                                  |
| 403              | Forbidden           | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |