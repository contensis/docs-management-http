---
description: A project resource can be retrieved from the Delivery API to understand the languages that the project supports and which language is the primary language.
---
# Project

A project resource can be retrieved from the Delivery API to understand the languages that the project supports and which language is the primary language.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| name | string |  | The friendly name given to the project. |
| description | string |  | The description text given to a project. |
| supportedLanguages | string [...] |  | An array of all the languages supported by the project. |
| primaryLanguage | string | [Language code](/localization.md)  | The primary language for the project. |


## Example

```json
{
    "id": "movieDb",
    "name": "Movie Database",
    "description": "...",
    "supportedLanguage": [
        "en-GB",
        "en-US",
        "fr"
    ],
    "primaryLanguage": "en-GB"
}

```
