---
description: A state that an entry is assigned to as part of its life cycle.
---
# Workflow definition state

A state that an entry can be assigned to as part of its life cycle.

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| id | string | | An identifier for the state, which must be unique within the workflow. |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to the state. |
| entryActions | object[] | [Action](actions) | Actions to be performed on the entry when it enters the current state. |
| events | object[] | [Event](/model/workflow-definitions/event.md) | A collection of events that can occur to an entry in this state. |
| color | string | [Color](colors) | The color to be displayed in the Contensis UI for the state. |
| uiEditorView | string | [Ui Editor View](ui-editor-view) | The view used by the Contensis UI to display the entry when it is in this state.  |

## Example

This example shows a workflow state.

```json
{
    "id": "awaitingApproval",
    "name": {
        "en-GB": "Awaiting approval"
    },
    "entryActions": [],
    "events": [{
            "id": "revoke",
            "name": {
                "en-GB": "Revoke and edit"
            },
            "description": {
                "en-GB": "Revoke the entry submission"
            },
            "transitionTo": "draft",
            "exitActions": [],
            "color": "blue",
            "groupId": "submitRevoke",
            "uiAction": "none",
            "parameters": []
        }, {
            "id": "decline",
            "name": {
                "en-GB": "Decline"
            },
            "description": {
                "en-GB": "Decline the entry for approval"
            },
            "transitionTo": "declined",
            "exitActions": [],
            "color": "red",
            "groupId": "approveDecline",
            "uiAction": "navigateToEntryListing",
            "parameters": [{
                    "id": "message",
                    "name": {
                        "en-GB": "Add a message to explain to the author why this content is being declined"
                    },
                    "dataType": "string",
                    "dataFormat": null,
                    "description": {
                        "en-GB": "The decline reason"
                    },
                    "default": null,
                    "validations": {
                        "required": {
                            "message": {
                                "en-GB": "The decline reason is required"
                            }
                        }
                    },
                    "editor": {
                        "id": "multiline",
                        "instructions": {
                            "en-GB": "Include a message to let an approver know your changes"
                        },
                        "properties": null
                    }
                }
            ]
        }, {
            "id": "approve",
            "name": {
                "en-GB": "Approve"
            },
            "description": {
                "en-GB": "Approve the entry changes for publishing"
            },
            "transitionTo": "versionComplete",
            "exitActions": [{
                    "invokeAction": "publishEntry"
                }
            ],
            "color": "green",
            "groupId": "approveDecline",
            "uiAction": "navigateToEntryListing",
            "parameters": []
        }, {
            "id": "sysDelete",
            "name": {},
            "description": {},
            "transitionTo": null,
            "exitActions": null,
            "color": "blue",
            "groupId": "delete",
            "uiAction": "none",
            "parameters": []
        }
    ],
    "color": "yellow",
    "uiEditorView": "previousPublishedVersionCompare"
}
```
