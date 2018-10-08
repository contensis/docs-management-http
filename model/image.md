---
description: An image type is a container of an image asset with an associated caption and alt text.
---
# Image

An image type is a container of an image asset with an associated caption and alt text.

## Properties

| Name            | Type   | Format                                                 | Description |
| :-------------- | :------| :----------------------------------------------------- | :---------- |
| asset           | object | [Asset](/model/link.md)                                | The asset that is linked to from the entry. |
| altText         | string |                                                        | The image alt text, defined in the entry. |
| caption         | string |                                                        | The image caption, defined in the entry. |
| transformations | object | Awaiting Image API documentation | The transformations that will be applied to the image. |

> **Note** The caption property allows instance specific text to be associated with a linked image asset.

## Example

```json
{
    "asset": {
        "sys": {
            "id": "a83c9fcc-51ef-41aa-878f-af5a33ba4b2f",
            "dataFormat": "asset",
            "language": "en-GB"
        }
    },
    "caption": "Fight club is a great film!",
    "altText": "The 1999 Fight Club image poster",
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
