---
description: A data type is the storage type for a field, and determines how the field data is validated and indexed for search.
---
# Data types

A data type is the storage type for a field, and determines how the field data is validated and indexed for search.

Contensis supports the following basic data types:

| Type | Description | Applicable Validations |
| :--- | :---------- | :--------------------- |
| string | Used for text entries such as titles, content or markup. | [required](/key-concepts/validations.md#required)<br/> [maxChars](/key-concepts/validations.md#maxchars)<br/> [minChars](/key-concepts/validations.md#minchars)<br/> [regex](/key-concepts/validations.md#regex)<br/> [allowedValues](/key-concepts/validations.md#allowedvalues)<br/> |
| integer | A whole number. | [required](/key-concepts/validations.md#required)<br/> [min](/key-concepts/validations.md#min)<br/> [max](/key-concepts/validations.md#max)<br/> |
| decimal | A number with a fractional part. | [required](/key-concepts/validations.md#required)<br/> [min](/key-concepts/validations.md#min)<br/> [max](/key-concepts/validations.md#max)<br/> [decimalPlaces](/key-concepts/validations.md#decimalplaces)<br/> |
| boolean | A value of *true* or *false*. | [required](/key-concepts/validations.md#required)<br/> |
| dateTime | A point in time. | [required](/key-concepts/validations.md#required)<br/> [min](/key-concepts/validations.md#min)<br/> [max](/key-concepts/validations.md#max)<br/> [pastDateTime](/key-concepts/validations.md#pastdatetime)<br/> |
| object | Any arbitrary structure as JSON or a string .| [required](/key-concepts/validations.md#required)<br/> |
| stringArray | An array of strings. | [required](/key-concepts/validations.md#required)<br/> [maxChars](/key-concepts/validations.md#maxchars)<br/> [minChars](/key-concepts/validations.md#minchars)<br/> [regex](/key-concepts/validations.md#regex)<br/> [allowedValues](/key-concepts/validations.md#allowedvalues)<br/> [maxCount](/key-concepts/validations.md#maxcount)<br/> [minCount](/key-concepts/validations.md#mincount)<br/> |
| integerArray | An array of integers. | [required](/key-concepts/validations.md#required)<br/> [maxCount](/key-concepts/validations.md#maxcount)<br/> [minCount](/key-concepts/validations.md#mincount)<br/>  |
| decimalArray | An array of decimals. | [required](/key-concepts/validations.md#required)<br/> [min](/key-concepts/validations.md#min)<br/> [max](/key-concepts/validations.md#max)<br/> [decimalPlaces](/key-concepts/validations.md#decimalplaces)<br/> [maxCount](/key-concepts/validations.md#maxcount)<br/> [minCount](/key-concepts/validations.md#mincount)<br/> |
| dateTimeArray | An array of dateTimes. | [required](/key-concepts/validations.md#required)<br/> [min](/key-concepts/validations.md#min)<br/> [max](/key-concepts/validations.md#max)<br/> [pastDateTime](/key-concepts/validations.md#pastdatetime)<br/> [maxCount](/key-concepts/validations.md#maxcount)<br/> [minCount](/key-concepts/validations.md#mincount)<br/>|
| objectArray | An array of objects. | [required](/key-concepts/validations.md#required)<br/> [maxCount](/key-concepts/validations.md#maxcount)<br/> [minCount](/key-concepts/validations.md#mincount)<br/> |


## Examples

```json
{
    "string": "This is a simple string",
    "integer": 24,
    "decimal": 1.34,
    "boolean": true,
    "dateTime": "2016-10-12T09:29:18.5144641+01:00",
    "object": {
        "id": "12345",
        "name": "item1"
    },
    "stringArray": [
        "Item 1",
        "Item 2",
        "Item 3"
    ],
    "integerArray": [
        1,2,3
    ],
    "decimalArray": [
        1.2, 3.4, 5.6
    ],
    "dateTimeArray": [
        "2017-03-07T14:37:27.0998174+00:00",
        "2017-03-07T14:39:16.3337294+00:00",
        "2017-03-07T14:39:19.3495296+00:00"
    ],
    "objectArray": [
        {
            "id": "12345",
            "name": "item1"
        },
        {
            "id": "67890",
            "name": "item2"
        }
    ]
}
```
