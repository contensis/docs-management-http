---
description: The transformation object represents a list of transformations that will be applied to the image using the Image API.
---
# Image Transformations

The transformation object represents a list of transformations that will be applied to the image using the Image API.

## Properties

| Name | Type   | Format | Description                         |
|:-----|:-------|:-------|:------------------------------------|
| w    | int    |        | The image width in pixels.          |
| h    | int    |        | The image height in pixels.         |
| flip | string |        | The orientation flip name to apply. |
| r    | int    |        | The image rotation in degrees.      |
| crop | string |        | The crop to apply.                  |
| q    | int    |        | The quality in percentage.          |

## Remarks

The order of the transformations should remain as documented here.

## Example

```json
{
  "poster": {
    "asset": {
      "sys": {
        "id": "fab3fdc6-89fd-4efa-bfe0-30722fb87661",
        "dataFormat": "asset"
      }
    },
    "caption": "Interstellar Movie Poster",
    "transformations": [
        {"w": 100},
        {"h": 200},
        {"flip": "v"},
        {"r": 0},
        {"crop": "500,300,center"},
        {"q": 100}
    ]
}
```
