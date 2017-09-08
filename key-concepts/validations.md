# Validations
Validations allow you to control the content which is entered within a field. Each validation has a set of properties which are described in more detail below. A common property across all validations is the message. Messages are optional on validations and if not specified, a default validation error message is returned from the API.

## Content validations
When creating, updating or publishing an entry, if a field has been populated then the value will be evaluated against the following validations. If the field hasn't been populated then the validation is ignored. This is to allow for partial completion of an entry when saving.

- [MaxLength](#maxlength)
- [MinLength](#minlength)
- [Min](#min)
- [Max](#max)
- [Regex](#regex)
- [AllowedValues](#allowedvalues)
- [AllowedFieldTypes](#allowedfieldtypes)
- [TaxonomyRoot](#taxonomyroot)
- [AllowedContentTypes](#allowedcontenttypes)
- [PastDateTime](#pastdatetime)
- [DecimalPlaces](#decimalplaces)
- [MaxCount](#maxcount)
- [MinCount](#mincount)


## Required validations
When publishing an entry, in addition to the above content validations, required validations are evaluated. If a required field hasn't been populated at this stage then the entry will fail to publish and a validation message will be returned.

- [Required](#required)
- [RequiredFields](#requiredfields)


## Required

### Description
Validates that a field value must be set.

### Applies to
All fields.

### Definition
```json
"validations": {
    "required": {
        "message": {
            "en-GB": "A value is required"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"A value is required"
      }
   ],
   "type":"Validation"
}
```

## MaxLength

### Description
Validates a maximum length for a string based field.

### Applies to
string, stringArray

### Definition

```json
"validations": {
    "maxLength": {
        "value": 50,
        "message": {
            "en-GB": "Maximum length of 50"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"Maximum length of 50"
      }
   ],
   "type":"Validation"
}
```

## MinLength

### Description
Validates a minimum length for a string based field.

### Applies to
string, stringArray

### Definition

```json
"validations": {
    "minLength": {
        "value": 10,
        "message": {
            "en-GB": "Minimum length of 10"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"Minimum length of 50"
      }
   ],
   "type":"Validation"
}
```

## Min

### Description
Validates a minimum value for a field.

### Applies to
integer, integerArray, decimal, decimalArray, dateTime, dateTimeArray

### Definition

```json
"validations": {
    "min": {
        "value": 5,
        "message": {
            "en-GB": "The value is too low. A minimum of 5 is required"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"The value is too low. A minimum of 5 is required"
      }
   ],
   "type":"Validation"
}
```
## Max

### Description
Validates a maximum value for a field.

### Applies to
integer, integerArray, decimal, decimalArray, dateTime, dateTimeArray

### Definition

```json
"validations": {
    "max": {
        "value": 100,
        "message": {
            "en-GB": "The value is too high. A maximum of 100 is allowed"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"The value is too high. A maximum of 100 is allowed"
      }
   ],
   "type":"Validation"
}
```

## Regex

### Description
Executes a regular expression on a string based field.

### Applies to
string, stringArray

### Definition

```json
"validations": {
    "regex": {
        "pattern": "[a-zA-Z]+",
        "message": {
            "en-GB": "The value does not match the regex"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"The value does not match the regex"
      }
   ],
   "type":"Validation"
}
```

## AllowedValues

### Description
Validates that only the allowed values have been set as the field value.

### Applies to
string, stringArray

### Definition

```json
"validations": {
    "allowedValues": {
        "values": [
            {
                "en-GB": "Red",
                "fr-FR": "Rouge"
            },
            {
                "en-GB": "Black",
                "fr-FR": "Noir"
            }
        ],
        "message": {
            "en-GB": "The selected value is not allowed",
            "fr-FR": "La valeur sélectionnée n'est pas autorisée."
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"The selected value is not allowed"
      }
   ],
   "type":"Validation"
}
```

## RequiredFields

### Description
Validates that a field is required in object types. For example, the source is required in the Quote field.

### Applies to
quote, image

### Definition

```json
"validations": {
    "requiredFields": {
        "fields": [
            {
                "name": "source",
                "message": {
                    "en-GB": "A source is required"
                }
            },
            {
                "name": "quote",
                "message": {
                    "en-GB": "A quote is required"
                }
            },
            {
                "name": "caption",
                "message": {
                    "en-GB": "An image caption is required"
                }
            }          
        ]
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"A source is required"
        },
        {  
         "field":"fieldId",
         "message":"A caption is required"
        }
   ],
   "type":"Validation"
}
```

## AllowedFieldTypes

### Description
Specifies which fields are available within a composer and validates that only those are set in the field value.

### Applies to
composer

### Definition

```json
"validations": {
    "allowedFieldTypes": {
        "fields": [
            {
                "id": "text",						
                "name": {
                    "en-GB": "Text"
                },
                "description": null,
                "dataType": "string",
                "dataFormat": "text",
                "validations": {}
            },
            {
               "id": "markup",
                "name": {
                    "en-GB": "Markup"
                },
                "description": null,
                "default": null,
                "dataType": "string",
                "dataFormat": "html",
                "validations": {}
            }      
        ],
        "message": {
            "en-GB": "The field type is not allowed"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
      {  
         "field":"fieldId",
         "message":"The field type is not allowed"
      }
   ],
   "type":"Validation"
}
```

## TaxonomyRoot

### Description
Specifies the root Taxonomy node that values can be selected from.

### Applies to
taxonomy, taxonomyArray

### Definition

```json
"validations": {
    "taxonomyRoot": {
        "key": "0/1/2",
        "message": {
            "en-GB": "The taxonomy code is not in the allowed root"        
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"The taxonomy code is not in the allowed root"
        }
   ],
   "type":"Validation"
}
```

## AllowedContentTypes

### Description
Specifies the allowed content type or asset types selectable in the field.

### Applies to
entry, entryArray, asset, assetArray

### Definition

```json
"validations": {
    "allowedContentTypes": {
        "contentTypes": [
            "PDF",
            "image"
        ],
        "message": {
            "en-GB": "The asset type is not allowed"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"The asset type is not allowed"
        }
   ],
   "type":"Validation"
}
```

## PastDateTime

### Description
Specifies that the date time value must be in the past. To allow future dates times, do not apply this validation to the field.

### Applies to
dateTime, dateTimeArray

### Definition

```json
"validations": {
    "pastDateTime": {
        "message": {
            "en-GB": "The date must be in the past"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"The date must be in the past"
        }
   ],
   "type":"Validation"
}
```

## DecimalPlaces

### Description
Validates how many decimal places a decimal based field value is allowed to have.

### Applies to
decimal, decimalArray

### Definition

```json
"validations": {
    "decimalPlaces": {
        "value": 3,
        "message": {
            "en-GB": "The value must be to 3 decimal places"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"The value must be to 3 decimal places"
        }
   ],
   "type":"Validation"
}
```

## MaxCount

### Description
Validates the maximum amount of elements an array type field can have.

### Applies to
booleanArray, dateTimeArray, decimalArray, integerArray, objectArray, stringArray

### Definition

```json
"validations": {
    "maxCount": {
        "value": 3,
        "message": {
            "en-GB": "The value cannot contain more ts 3 elements"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"The value cannot contain more ts 3 elements"
        }
   ],
   "type":"Validation"
}
```

## MinCount

### Description
Validates the minimum amount of elements an array type field can have.

### Applies to
booleanArray, dateTimeArray, decimalArray, integerArray, objectArray, stringArray

### Definition

```json
"validations": {
    "minCount": {
        "value": 3,
        "message": {
            "en-GB": "The value cannot contain less ts 3 elements"
        }
    }
}
```
### Example response

```json
{  
   "logId":"64d3dd41-9c6d-4ecd-a275-628bb4f9bc21",
   "message":"There are validation errors creating the entry",
   "data":[  
        {  
            "field":"fieldId",
            "message":"The value cannot contain less ts 3 elements"
        }
   ],
   "type":"Validation"
}
```