---
description: A parameter which defines a message to be displayed in the Contensis UI when a workflow event is triggered, and validation to be performed.
---
# Workflow definition event parameter

A parameter which defines a message to be displayed in the Contensis UI when a workflow event is triggered, and validation to be performed.

Currently the only editor supported for use in workflow definitions is the *multiline* [editor](editor), which displays a customisable message to the user when the parent event is triggered to prompt the user to enter text, e.g. when submitting an entry for approval.

This editor can be used in conjunction with the *required* [validation](validation) to make entering text mandatory.

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| id | string | | The identifier for the parameter. |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to the parameter.|
| description | object | [Localized value](/key-concepts/localization.md)  | The description given to the parameter.|
| dataType | string | | This should be set to *"string"*. |
| dataType | string | | This should be set to *null*. |
| default | object | | This should be set to *null*. |
| validations | object[] | [Validation](validation)  | The validation to be used. |
| editor | object | [editor](editor) | The editor to be used. | 

## Example

This example shows a parameter as used in a workflow definition.

```json
{
    "id": "message",
    "name": {
        "en-GB": "Add an optional message for the approver"
    },
    "description": {
        "en-GB": "The message included with the entry submission"
    },
    "dataType": "string",
    "dataFormat": null,
    "default": null,
    "validations": {
        "required": {
            "message": {
                "en-GB": "The reason is required"
            }
        }
    },
    "editor": {
        "id": "multiline",
        "instructions": {
            "en-GB": "Optionally include a message to let an approver understand your changes"
        },
        "properties": null
    }
}
```
