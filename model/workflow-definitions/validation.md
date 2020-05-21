---
description: A validation for a workflow event parameter.
---
# Workflow definition event validation

A validation for a workflow event parameter.

Currently the only validation supported for use in workflow definitions is the *required* validation, which can be used in conjunction with the *multiline* [editor](editor) to validate that the user enters some text when the parent event is triggered, e.g. when submitting an entry for approval.

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| message | object | [Localized value](/key-concepts/localization.md)  | A message to be displyed in the Contensis UI if the validation fails. |

## Example

This example shows the *required* validation as used in a workflow definition.

```json
{
    "required": {
        "message": {
            "en-GB": "The reason is required"
        }
}
```
