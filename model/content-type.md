# Content type

A content type determines the schema of an [entry](/model/entry.md). Entries are constructed and validated using the information defined in the fields collection.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | | A unique content type identifier |
| projectId | string |  | The project identifier |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to a content type |
| description | object | [Localized value](/key-concepts/localization.md) | The description text given to a content type |
| entryTitleField | string |  | The id of the field which should be used as the title in entry listings |
| fields | object [...] | [Field](#field)  | A collection of fields that form the schema for an entry |
| enabled | boolean |  |  |
| defaultLanguage | string | [Language code](/key-concepts/localization.md) |  |
| supportedLanguages | string [...] | [Language code](/key-concepts/localization.md) |  |
| workflowId | string |  | The workflow that derived entries will  |
| dataFormat | string |  | Either *entry* or *asset* |
| previewUrl | string |  | The url that an example of an entry based on the content type can be viewed |
| version | object | [Version](/model/version.md) | Version information about the content type |

## Field

The field object is the definition of a field within an entry. The field also contains the validations and editor configuration that is used within the Contensis UI and services.

### Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string |  | A unique field identifier |
| name | object | [Localized value](/key-concepts/localization.md) | A friendly name for the field |
| description | object | [Localized value](/key-concepts/localization.md) | The description for the field's purpose |
| dataType | string | [Data type](/key-concepts/data-types.md) | The field data type |
| dataFormat | string | [Data type](/key-concepts/data-formats.md) | The field data format |
| default | object | [Localized value](/key-concepts/localization.md) | The default value for the field if no value is provided by an editor |
| validations | object |  | The validations that will be performed on the field when the entry is either created or updated |
| editor | object | Editor | Configuration for the Contensis entry editor |

## Localized value
A localized value is a object that has values that are keyed by [language codes](/key-concepts/localization.md) which allows multilingual variations of a specific property.

## Example

```json
{
  "id": "movie",
  "projectId": "website",
  "name": {
    "en-GB": "Movie"
  },
  "description": {
    "en-GB": "A movie type"
  },
  "entryTitleField": "title",
  "fields": [
    {
      "id": "title",
      "name": {
        "en-GB": "Title"
      },
      "dataType": "String",
      "dataFormat": null,
      "description": {},
      "default": {},
      "validations": null,
      "editor": {
        "id": "text",
        "instructions": {
          "en-GB": "The title of the movie"
        },
        "properties": {
          "placeholderText": {
            "en-GB": "Enter the full title of the movie appropriate to the region"
          }
        }
      }
    },
    {
      "id": "tagline",
      "name": {
        "en-GB": "Tagline"
      },
      "dataType": "String",
      "dataFormat": null,
      "description": {},
      "default": {},
      "validations": null,
      "editor": null
    },
    {
      "id": "overview",
      "name": {
        "en-GB": "Overview"
      },
      "dataType": "String",
      "dataFormat": "html",
      "description": {},
      "default": {},
      "validations": null,
      "editor": null
    },
    {
      "id": "releaseDate",
      "name": {
        "en-GB": "Release Date"
      },
      "dataType": "dateTime",
      "dataFormat": null,
      "description": {},
      "default": {},
      "validations": null,
      "editor": {
        "id": "date",
        "instructions": {
          "en-GB": "The release date of the movie"
        },
        "properties": {}
      }
    },
    {
      "id": "actors",
      "name": {
        "en-GB": "Actors"
      },
      "dataType": "ObjectArray",
      "dataFormat": "entry",
      "description": {},
      "default": {},
      "validations": {
        "contentType": {
          "contentType": "dan"
        }
      },
      "editor": {
        "id": "entry",
        "instructions": {
          "en-GB": ""
        },
        "properties": {
          "placeholderText": {
            "en-GB": "Add the main actors"
          }
        }
      }
    }
  ],
  "enabled": true,
  "defaultLanguage": "en-GB",
  "supportedLanguages": [
    "en-GB",
    "fr-FR",
    "de-DE",
    "es"
  ],
  "workflowId": "ContensisMultilingual",
  "dataFormat": "entry",
  "previewUrl": "http://www.mymoviewebsite.com/movies/terminator",
  "version": {
        "createdBy": "s.derrickson",
        "created": "2016-10-12T09:29:18.5144641+01:00",
        "modifiedBy": "b.cumberbatch",
        "modified": "2016-10-13T10:15:12.1973648+01:00",
        "publishedBy": "b.cumberbatch",
        "published": "2016-10-13T10:15:12.1973648+01:00",
        "versionNo": "2.0"
    }
}
```
