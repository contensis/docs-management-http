---
description: An editor which is displayed in the Contensis UI for a workflow event.
---
# Workflow definition event editor

An editor which is displayed in the Contensis UI for a workflow event.

Currently the only editor supported for use in workflow definitions is the *multiline* editor, which displays a customisable message to the user when the parent event is triggered to prompt the user to enter text, e.g. when submitting an entry for approval. This editor can be used in conjunction with the *required* [validation](validation) to make entering text mandatory.

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| id | string | | The identifier for the editor. This should be set to *"multiline"* for the *mulitline* editor. |
| instructions | object | [Localized value](/key-concepts/localization.md)  | Instructions to be displyed in the Contensis UI when the parent event is triggered. |
| properties | object | | This should be set to *null*. | 

## Example

This example shows the *multiline* editor as used in a workflow definition.

```json
{
    "id": "multiline",
    "instructions": {
        "en-GB": "Optionally include a message to let an approver understand your changes"
}
```
