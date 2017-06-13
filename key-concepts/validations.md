# Validations

## Create/Update
Validations are only executed on entry create and update when a value has been set. If there is no value set, the validation is ignored.
- [MaxLength](#maxlength)
- [MinLength](#minlength)
- [Min](#min)
- [Max](#max)
- [Regex](#regex)
- [AllowedValues](#allowedvalues)
- [AllowedFieldTypes](#allowedfieldtypes)
- [TaxonomyRoot](#taxonomyroot)
- [AllowedContentTypes](#allowedcontenttypes)
- [AllowedDates](#alloweddates)
- [DecimalPlaces](#decimalplaces)
- [MaxCount](#maxcount)
- [MinCount](#mincount)


## Publish
All validations are always executed on entry publish.
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

```http
Validation error response here
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

```http
Validation error response here
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

```http
Validation error response here
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

```http
Validation error response here
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

```http
Validation error response here
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

```http
Validation error response here
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
            "en-GB": "The selected value is not allowed.",
            "fr-FR": "La valeur sélectionnée n'est pas autorisée."
        }
    }
}
```
### Example response

```http
Validation error response here
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
                "name": "Source",
                "message": {
                    "en-GB": "A source is required"
                }
            },
            {
                "name": "Quote",
                "message": {
                    "en-GB": "A quote is required"
                }
            },
            {
                "name": "Caption",
                "message": {
                    "en-GB": "An image caption is required"
                }
            }          
        ]
    }
}
```
### Example response

```http
Validation error response here
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

```http
Validation error response here
```

## TaxonomyRoot

### Description
Specifies the root Taxonomy node that values can be selected from.

### Applies to
taxonomy, taxonomyArray

### Definition

```json
"validations": {
    "key": "0/1/2",
    "message": {
        "en-GB": "The taxonomy code is not in the allowed root"        
    }
}
```
### Example response

```http
Validation error response here
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

```http
Validation error response here
```

## AllowedDates

### Description
Specifies the allowed selectable date tense - Either past or future. To allow all dates, do not apply this validation to the field.

### Applies to
dateTime, dateTimeArray

### Definition

```json
"validations": {
    "allowedDates": {
        "value": "past" | "future",
        "message": {
            "en-GB": "The date must be in the past"
        }
    }
}
```
### Example response

```http
Validation error response here
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

```http
Validation error response here
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
            "en-GB": "The value cannot contain more than 3 elements"
        }
    }
}
```
### Example response

```http
Validation error response here
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
            "en-GB": "The value cannot contain less than 3 elements"
        }
    }
}
```
### Example response

```http
Validation error response here
```