---
description: The entry usage content type info object contains a subset of content type data to describe links to an entry. 
---
# Entry usage content type info

The entry usage content type info object contains a subset of content type data to describe links to an entry. This is used when [retrieving a list of content types which have entries linking to an entry](/entries/entry-usage-content-types.md).

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | | The unique content type identifier. |
| name | object | [Localized value](/key-concepts/localization.md) | The friendly name given to the content type. |
| count | integer | | The count of linked entries for the content type. |

## Example

This JSON example shows an entry usage content type info object based on a linked actor entry.

```json
{
    "id": "person",
    "name": "Jennifer Lawrence",
    "count": 12
}
```
