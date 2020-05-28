---
description: A grouping for events in workflow definition states.
---
# Workflow definition event group

Groups which [events](event) in workflow [states](state) are assigned to. These group functionally similar transitions between states (e.g. *save*, *approveDecline*, *delete*).

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| id | string | | An identifier for the event group, which must be unique within the workflow. |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to the event group. |

## Example

This example shows an event group.

```json
{
    "id": "save",
    "name": {
        "en-GB": "Save"
    }
}
```
