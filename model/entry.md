---
description: An entry definition in the Management API contains a mixture of standard properties and properties that have been defined by the content type that an entry is based on.
---
# Entries

An entry definition in the Management API contains a mixture of standard properties and properties that have been defined by the content type that an entry is based on.

## Data properties

Data properties are items defined by the [fields collection](/model/content-type.md#field) set in a content type.

## Standard properties

These are the standard properties that all entries have. The language property is the indexer for the entry data as an entry can have multiple language variations which can be be edited and versioned independently. In the Delivery API context only a single language variation is available on an entry.

### Entry

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| field id | Any | Any | Field data that is defined in the associated [content type](/model/content-type.md#field). The data is keyed by a unique field id.  |
| sys | object | [Sys](#sys) | The container of the entry system data. |

### Sys

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | GUID | The entry identifier as a 128 bit GUID. |
| projectId | string | | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| contentTypeId | string | | The API identifier of the content type that the entry is based on. |
| dataFormat | string | | Either *entry* or *asset*. |
| language | string | [Language code](/localization.md) | The language code of the entry variation. |
| availableLanguages | string[] | [Language code](/localization.md) | A list languages which have available translations. |
| unavailableLanguages | string[] | [Language code](/localization.md) | A list languages which the entry can be translated to but have yet to be completed. |
| uri | string | URI | The entry uri. |
| metadata | object | | Metadata associated with the entry instance. |
| workflow | object | | Workflow associated with the entry instance. |
| workflow.id | string | | The API identifier of the workflow that the entry is using. |
| workflow.state | string | | The API identifier of the current workflow state of the entry. |
| workflow.allowedEvents | string[] | | A list of workflow events which can be carried out from the current state. |
| workflow.transition | object | | Transition data associated with the last workflow transition. |
| workflow.data | string | | Data which has been supplied for the current transition. e.g. Declined reason. |
| workflow.invoked | string | | When the transition took place. |
| workflow.from | string | | Which state the entry transitioned from. |
| workflow.invokedBy | string | | Who invoked the workflow transtion. |
| workflow.event | string | | The workflow event which triggered the transition. |
| isPublished | boolean | | If the entry is currently pubished then the value will be *true*. If the entry has yet to be published or has been unpublished it will be *false*. |
| translationState | string | | The API identifier of the translation status of the entry. Possible values are *None, NeverTranslated, Translated, TranslationOutOfDate, NoDefaultLanguage, AvailableForTranslation, NotAvailableForTranslation*|
| version | object | [Version](/model/version.md) | Version info specific to the entry variation. |


## Example

This JSON example shows entry based on a movie content type.

```json
{
    "title": "Back to the future",
    "tagline": "He's the only kid ever to get into trouble before he was born.",
    "overview": "Marty McFly, a typical American teenager of the Eighties, is accidentally sent back to 1955 in a plutonium-powered DeLorean \"time machine\" invented by slightly mad scientist. During his often hysterical, always amazing trip back in time, Marty must make certain his teenage parents-to-be meet and fall in love - so he can get back to the future.",
    "trailer": "https://www.youtube.com/watch?v=qvsgGtivCgs",
    "releaseDate": "1985-07-02T23:00:00Z",
    "actors": [
        {
            "sys": {
                "id": "a1c983d6-4aaf-4456-9f3d-a6eac3139f1c",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        },
        {
            "sys": {
                "id": "16f6f2de-e901-4bda-bf3f-092b93ae62a9",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        },
        {
            "sys": {
                "id": "09b87c0b-67b2-4028-9358-e29ff16f11da",
                "language": "en-GB",
                "dataFormat": "entry"
            }
        }
    ],

    "sys": {
        "id": "71f73a9b-2a13-4d63-bcc1-e8ee5047b01c",
        "contentTypeId": "movie",
        "projectId": "movieDb",
        "language": "en-GB",
        "availableLanguages": [
            "en-GB",
            "fr"
        ],
        "unavailableLanguages": [
            "de"
        ],
        "uri": "/api/management/projects/movieDb/entries/71f73a9b-2a13-4d63-bcc1-e8ee5047b01c",
        "dataFormat": "entry",
        "metadata": {},
        "workflow": {
            "id": "contensisEntryBasic",
            "state": "versionComplete",
            "allowedEvents": [
                "versionComplete.sysUpdate",
                "versionComplete.sysDelete",
                "sysUnpublish"
            ],
            "transition": {
                "data": null,
                "invoked": "2020-03-24T14:51:35.8923327Z",
                "from": "draft",
                "invokedBy": "zengenti",
                "event": "publish"
            }
        },
        "isPublished": true,
        "translationState": "Translated",
        "version": {
            "createdBy": "s.derrickson",
            "created": "2016-10-12T09:29:18.5144641+01:00",
            "modifiedBy": "b.cumberbatch",
            "modified": "2020-03-24T14:51:35.7048498Z",
            "publishedBy": "b.cumberbatch",
            "published": "2020-03-24T14:51:35.8610917Z",
            "versionNo": "2.0"
        }
    }
}
```
