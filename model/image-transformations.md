---
description: The transformation object represents the transformations that will be applied to the image using the Image API.
---
# Image Transformations

The transformation object represents the transformations that will be applied to the image using the Image API.

## Properties

| Name    | Type   | Description                                                                  |
|:--------|:-------|:---------------------------------------------------------------------------- |
| size    | object | The image height and width resize transformations                           |
| flip    | string | The orientation flip name to apply                                          |
| rotate  | int    | The image rotation in degrees                                               |
| crop    | object | The image crop details specifying width and height, and x and y coordinates |
| quality | int    | The quality in percentage                                                   |

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
    "transformations": {  
        "size": {  
            "height": 100,
            "width": 100
        },
        "flip": "h",
        "rotate": 95,
        "crop": {  
            "width": 100,
            "height": 100,
            "x": 10,
            "y": 20
        },
        "quality": 95
    }
}
```