# Image
An image type is a container of an image asset with an associated caption.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| asset | object | [Asset](/model/link.md) | The asset that is linked to from the entry |
| caption | string |  | The image caption, defined in the entry |

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
    "caption": "Fight club is a great film!"
}
```
