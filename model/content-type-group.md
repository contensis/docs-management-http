---
description: The content type group object represents a group of related fields.
---
# Content type group

The content type group object enables related fields to be grouped together in the UI.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :-- | :---------- |
| id   | string |                                                  | A group identifier which is unique within the content type |
| name | object | [Localized value](/key-concepts/localization.md) | The friendly name given to the content type group          |

## Example

```json
{
    "id": "mainContent",
    "name": {
        "en-GB": "Main content"
    }
}
```
