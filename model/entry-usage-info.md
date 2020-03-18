---
description: The entry usage info object contains a subset of entry data to describe an entry. 
---
# Entries

The entry usage info object contains a subset of entry data to describe an entry. This is used when [retrieving a list of entries which link to an entry](/entries/entry-usage.md)

## Properties

Data properties are items defined by the [fields collection](/model/content-type.md#field) set in a content type.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | GUID | The entry identifier as a 128 bit GUID. |
| title | string | | The title of the linked entry. |
| description | string | | The description of the linked entry. |
| fieldId | string | | The API identifier of the field where the entry is linked from. |
| contentTypeId | string | | The API identifier of the content type that the linked entry is based on. |
| dataFormat | string | | Either *entry* or *asset*. |
| language | string | [Language code](/localization.md) | The language code of the entry variation. |


## Example

This JSON example shows an entry usage info object based on a linked actor entry.

```json
{
    "id": "3995f92c-2b3c-45bb-b2a6-1f1b6314be7a",
    "title": "Brad Pitt",
    "description": "William Bradley \"Brad\" Pitt (born December 18, 1963) is an American actor and film producer.",
    "fieldId": "actor",
    "contentTypeId": "actor",
    "dataFormat": "entry",
    "language": "en-GB"
}
```
