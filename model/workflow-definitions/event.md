---
description: An event that can occur to an entry while it is in the current workflow state.
---
# Workflow definition event

An event that can occur to an entry while it is in the current workflow state. This may cause the entry to transition to a different workflow state or stay in the same state.

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| id | string | | An identifier for the event, which must be unique within the workflow state. |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to the event. |
| description | object | [Localized value](/key-concepts/localization.md)  | The description given to the event.|
| transitionTo | string | | The identifier for the state that the event causes the entry to transition to. If this is not specified or set to *null* then the entry will remain in the same state when this event is triggered. |
| exitActions | object[] | [Action](actions) | Actions to be performed on the entry when the event triggers and the entry leaves the current state. |
| color | string | [Color](colors) | The color to be displayed in the Contensis UI for the event. |
| groupId | string | | The identifier of the workflow [event group](event-group) which the event belongs to. |
| uiAction | string |  | The event to be performed by the Contensis UI when an entry exits the workflow state. Currently on the value *"navigateToEntryListing"* is supported. The default is for no action to occur. |
| parameters | object[] | [Parameter](parameter) | Defines a message to be displayed in the Contensis UI when a workflow event is triggered, and validation to be performed. |

## Example

This example shows an event.

```json
{
    "id": "submit",
    "name": {
        "en-GB": "Send for approval"
    },
    "description": {
        "en-GB": "Send the entry for approval"
    },
    "transitionTo": "awaitingApproval",
    "exitActions": [
        {
        "invokeAction": "validateEntry"
        }
    ],
    "color": "blue",
    "groupId": "submitRevoke",
    "uiAction": "navigateToEntryListing",
    "parameters": [
        {
            "id": "message",
            "name": {
                "en-GB": "Add an optional message for the approver"
            },
            "dataType": "string",
            "dataFormat": null,
            "description": {
                "en-GB": "The message included with the entry submission"
            },
            "default": null,
            "validations": {},
            "editor": {
                "id": "multiline",
                "instructions": {
                    "en-GB": "Optionally include a message to let an approver understand your changes"
                },
                "properties": null
            }
        }
    ]
}
```
