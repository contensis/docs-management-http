---
description: A content type determines the schema of an entry.
---
# Content type

A content type determines the schema of an [entry](/model/entry.md). Entries are constructed and validated using the information defined in the fields collection.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | | A unique content type identifier |
| projectId | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to a content type |
| description | object | [Localized value](/key-concepts/localization.md) | The description text given to a content type |
| entryTitleField | string |  | The id of the field which should be used as the title in entry listings |
| entryDescriptionField | string |  | The id of the field which should be used as the description in entry listings |
| fields | object [...] | [Field](#field)  | A collection of fields that form the schema for an entry |
| groups | object [...] | [Content type group](/model/content-type-group.md) | A collection of groups that enable related fields to be grouped together in the UI |
| enabled | boolean |  |  |
| defaultLanguage | string | [Language code](/key-concepts/localization.md) |  |
| supportedLanguages | string [...] | [Language code](/key-concepts/localization.md) |  |
| workflowId | string |  | The workflow that derived entries will follow  |
| dataFormat | string |  | Either *entry* or *asset* |
| previewUrl | string |  | The URL where an example of an entry based on the content type can be viewed |
| defaultRendererId | GUID |  | The ID for the default renderer for the content type. Null if there is no default renderer |
| defaultParentNodeId | GUID |  | The ID for the default parent node for the content type. Null if there is no default parent node |
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
| dataFormat | string | [Data format](/key-concepts/data-formats.md) | The field data format |
| default | object | [Localized value](/key-concepts/localization.md) | The default value for the field if no value is provided by an editor |
| validations | object |  | The validations that will be performed on the field when the entry is either created or updated |
| editor | object | Editor | Configuration for the Contensis entry editor |
| groupId | string |  | The identifier of the group (defined in the content type groups property) that the field belongs to. Enables related fields to be grouped together in the UI |

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
  "entryDescriptionField": "overview",
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
        },
        "groupId": "summary"
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
      "editor": null,
      "groupId": null
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
      "editor": null,
      "groupId": "additionalInfo"
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
      },
      "groupId": "summary"
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
      },
      "groupId": "additionalInfo"
    }
  ],
  "groups": [
      {
          "id": "summary",
          "name": {
              "en-GB": "Main summary fields"
          }
      },
      {
          "id": "additionalInfo",
          "name": {
              "en-GB": "Additional Information"
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
  "defaultRendererId": "F1A7ABD5-9241-4FBD-AD1C-E1F46B6F6D44",
  "defaultParentNodeId": "3C7361CD-58A0-46CD-A414-F6D105BD8454",
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
