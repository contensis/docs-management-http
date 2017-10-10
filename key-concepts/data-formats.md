# Data formats

The data format property is used as an extension of a [data type](/key-concepts/data-types.md) to describe the structure and intent of the data. For example, a *location* has a data type of *object*, and a data format of *location*. Another example is a HTML block, which has a data type of *string* and a data format of *html*.  

The data format is a string value and is designed to allow custom types to be added.

## Supported data formats

The following list contains the data formats that are currently understood by Contensis:

| Data format | Data type | Description | Applicable Validations |
| :---------- | :-------- | :---------- | :--------------------- |
| [entry](/model/entry.md) | object | An entry format for storing content. | [required](/key-concepts/validations.md#required)<br/> [allowedContentTypes](/key-concepts/validations.md#allowedcontenttypes)<br/> |
| asset | object | An asset format that represents a file resource. | [required](/key-concepts/validations.md#required)<br/> [allowedContentTypes](/key-concepts/validations.md#allowedcontenttypes)<br/> |
| [location](/model/location.md) | object | Represents a point on the surface of the Earth. | [required](/key-concepts/validations.md#required)<br/> |
| [quote](/model/quote.md) | object | A quote with text and a source. | [required](/key-concepts/validations.md#required)<br/> [requiredFields](/key-concepts/validations.md#requiredfields)<br/>  |
| [dateRange](/model/date-range.md) | object | Represents a range of date times. | [required](/key-concepts/validations.md#required)<br/> [min](/key-concepts/validations.md#min)<br/> [max](/key-concepts/validations.md#max)<br/> [pastDateTime](/key-concepts/validations.md#pastdatetime)<br/>|
| [image](/model/image.md) | object | Wraps an Asset with an additional caption property. | [required](/key-concepts/validations.md#required)<br/> [requiredFields](/key-concepts/validations.md#requiredfields)<br/> |
| field | objectArray | Represents a [composed](/model/composed.md) type, defined as an objectArray data type. | [required](/key-concepts/validations.md#required)<br/>  [allowedFieldTypes](/key-concepts/validations.md#allowedfieldtypes)
| component.* | object | Represents a [component](/key-concepts/components.md) type. The asterisk represents the component id.| [required](/key-concepts/validations.md#required)<br/>  [allowedFieldTypes](/key-concepts/validations.md#allowedfieldtypes)<br/> |
| heading | string | Represents a document heading. | [required](/key-concepts/validations.md#required)<br/> |
| html | string | A string of HTML markup. | [required](/key-concepts/validations.md#required)<br/> |
| markdown | string | A string of markdown markup. | [required](/key-concepts/validations.md#required)<br/> |
