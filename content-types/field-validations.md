---
description: Field validations allow you to control the content which is entered within a field.  
---
# Field validations

Field validations allow you to control the content which is entered within a field. Each validation has a set of properties which are described in more detail below. A common property across all validations is the message. Messages are optional on validations and if not specified, a default validation error message is returned from the API.

## Content validations

When creating, updating or publishing an entry, if a field has been populated then the value will be evaluated against the following validations. If the field hasn't been populated then the validation is ignored. This is to allow for partial completion of an entry when saving.

* [MaxLength](#maxlength)
* [MinLength](#minlength)
* [Min](#min)
* [Max](#max)
* [Regex](#regex)
* [AllowedValues](#allowedvalues)
* [AllowedFieldTypes](#allowedfieldtypes)
* [TaxonomyRoot](#taxonomyroot)
* [AllowedContentTypes](#allowedcontenttypes)
* [PastDateTime](#pastdatetime)
* [DecimalPlaces](#decimalplaces)
* [MaxCount](#maxcount)
* [MinCount](#mincount)


## Required validations

When publishing an entry, in addition to the above content validations, required validations are evaluated. If a required field hasn't been populated at this stage then the entry will fail to publish and a validation message will be returned.

* [Required](#required)
* [RequiredFields](#requiredfields)

## Allowed validations for field types

<table width="100%">
    <tr>
        <th>DataType</th>
        <th>DataFormat</th>
        <th>Validations</th>
    </tr>
    <tr>
        <td rowspan="3">string</td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#maxlength">MaxLength</a><br />
            <a href="#minlength">MinLength</a><br />
            <a href="#regex">RegEx</a><br />
            <a href="#allowedvalues">AllowedValues</a>
        </td>
    </tr>
    <tr>
        <td>taxonomy</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#taxonomyroot">TaxonomyRoot</a>
        </td>
    </tr>
    <tr>
        <td>markup</td>
        <td>
            <a href="#required">Required</a>
        </td>
    </tr>
    <tr>
        <td rowspan="2">stringArray</td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#maxlength">MaxLength</a><br />
            <a href="#minlength">MinLength</a><br />
            <a href="#regex">RegEx</a><br />
            <a href="#allowedvalues">AllowedValues</a><br />
            <a href="#maxcount">MaxCount</a><br />
            <a href="#mincount">MinCount</a>
        </td>
    </tr>
    <tr>
        <td>taxonomy</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#taxonomyroot">TaxonomyRoot</a><br />
            <a href="#maxcount">MaxCount</a><br />
            <a href="#mincount">MinCount</a>
        </td>
    </tr>
    <tr>
        <td>
            integer
        </td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#max">Max</a><br />
            <a href="#min">Min</a>
        </td>
    </tr>
    <tr>
        <td>
            integerArray
        </td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#max">Max</a><br />
            <a href="#min">Min</a><br />
            <a href="#maxcount">MaxCount</a><br />
            <a href="#mincount">MinCount</a>
        </td>
    </tr>
    <tr>
        <td>
            decimal
        </td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#max">Max</a><br />
            <a href="#min">Min</a><br />
            <a href="#decimalplaces">DecimalPlaces</a><br />
            <a href="#maxcount">MaxCount</a><br />
            <a href="#mincount">MinCount</a>
        </td>
    </tr>
    <tr>
        <td>
            decimalArray
        </td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#max">Max</a><br />
            <a href="#min">Min</a><br />
            <a href="#decimalplaces">DecimalPlaces</a>
        </td>
    </tr>
    <tr>
        <td>
            datetime
        </td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#max">Max</a><br />
            <a href="#min">Min</a><br />
            <a href="#pastdatetime">PastDateTime</a>
        </td>
    </tr>
    <tr>
        <td rowspan="3">object</td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
        </td>
    </tr>
    <tr>
        <td>image, quote</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#requiredfields">RequiredFields</a>
        </td>
    </tr>
    <tr>
        <td>entry, asset</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#requiredfields">RequiredFields</a>
        </td>
    </tr>
    <tr>
        <td rowspan="3">objectArray</td>
        <td>&nbsp;</td>
        <td>
            <a href="#required">Required</a><br />
        </td>
    </tr>
    <tr>
        <td>field (composer)</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#allowedcontenttypes">AllowedContentTypes</a>
        </td>
    </tr>
    <tr>
        <td>entry, asset</td>
        <td>
            <a href="#required">Required</a><br />
            <a href="#requiredfields">RequiredFields</a><br />
            <a href="#maxcount">MaxCount</a><br />
            <a href="#mincount">MinCount</a>
        </td>
    </tr>
</table>                                                      

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
            "fr-FR": "La valeur sélectionnée n'est pas autorisée"
        }
    }
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

## TaxonomyRoot

### Description

Specifies the root taxonomy node that values can be selected from.

### Applies to

taxonomy, taxonomyArray

### Definition

```json
"validations": {
    "taxonomyRoot": {
        "key": "0/1/2",
        "message": {
            "en-GB": "The taxonomy node is not a descendant of the allowed root"
        }
    }
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

## MaxCount

### Description

Validates the maximum amount of elements an array type field can have.

### Applies to

dateTimeArray, decimalArray, integerArray, objectArray, stringArray

### Definition

```json
"validations": {
    "maxCount": {
        "value": 3,
        "message": {
            "en-GB": "The value cannot contain more than 3 node keys"
        }
    }
}
```

## MinCount

### Description

Validates the minimum amount of elements an array type field can have.

### Applies to

dateTimeArray, decimalArray, integerArray, objectArray, stringArray

### Definition

```json
"validations": {
    "minCount": {
        "value": 3,
        "message": {
            "en-GB": "The value cannot contain less than 3 node keys"
        }
    }
}
```
