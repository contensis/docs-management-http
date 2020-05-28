---
description: A workflow definition defines the life cycle for entries.
---
# Workflow definition

A workflow definition defines the life cycle for entries.

Every content type is assigned a workflow. All entries created for that content type will then follow the life cycle defined in that workflow definition.

Contensis supports two predefined workflow definitions (*contensisEntryBasic* and *contensisEntryApproval*) - see [here](https://developer.zengenti.com/contensis/api/management/dotnet/key-concepts/workflow.html). These cannot be modified, but additional custom workflows can be defined.

A workflow definition consists of a collection of [states](/model/workflow-definitions/state.md) which an entry assigned to that workflow may have (e.g. *draft*, *awaiting Approval*, *versionComplete*).
Each state consists of a collection of [events](/model/workflow-definitions/event.md), which define the allowed transitions from that state to other (or the same) states. The events are grouped into [event groups](/model/workflow-definitions/event-group.md), which group functionally similar transitions between states (e.g. *save*, *approveDecline*, *delete*).

Custom workflows are project-specific, i.e. each one only applies to one project, not all projects in a Contensis instance.

## Properties

| Name     | Type   | Format          | Description                                        |
|----------|--------|-----------------|----------------------------------------------------|
| id | string | | A unique workflow definition identifier. |
| uuid | string | GUID | The workflow definition identifier as a 128 bit GUID. |
| projectId | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| name | object | [Localized value](/key-concepts/localization.md)  | The friendly name given to the workflow definition. |
| description | object | [Localized value](/key-concepts/localization.md) | The description text given to the workflow definition. |
| states | object[] | [State](/model/workflow-definitions/state.md) | A collection of states that an entry with the workflow definition may have. |
| eventGoups | object[] | [Event group](/model/workflow-definitions/event-group.md) | A collection of event groups for events within the states. |
| isSystem | boolean | | Indicates whether the workflow definition is predefined and read only (true) or a custom definition (false). |
| version | object | [Version](/model/version.md) | Version information about the workflow definition. |

## Example

This example shows a workflow definition.

```json
{
    "uuid": "ab08e6c8-a883-4d59-960d-eb0cdc75840f",
    "id": "approvalWorkflow",
    "projectId": "",
    "name": {
        "en-GB": "Approval workflow"
    },
    "description": {
        "en-GB": "The default workflow for entries with approval"
    },
    "states": [{
            "id": "draft",
            "name": {
                "en-GB": "Draft"
            },
            "entryActions": [],
            "events": [{
                    "id": "sysUpdate",
                    "name": {
                        "en-GB": "Save"
                    },
                    "description": {},
                    "transitionTo": null,
                    "exitActions": null,
                    "color": "blue",
                    "groupId": "save",
                    "uiAction": "none",
                    "parameters": []
                }, {
                    "id": "submit",
                    "name": {
                        "en-GB": "Send for approval"
                    },
                    "description": {
                        "en-GB": "Send the entry for approval"
                    },
                    "transitionTo": "awaitingApproval",
                    "exitActions": [{
                            "invokeAction": "validateEntry"
                        }
                    ],
                    "color": "blue",
                    "groupId": "submitRevoke",
                    "uiAction": "navigateToEntryListing",
                    "parameters": [{
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
            "color": "cyan",
            "uiEditorView": "default"
        }, {
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
        }, {
            "id": "declined",
            "name": {
                "en-GB": "Declined"
            },
            "entryActions": [],
            "events": [{
                    "id": "sysUpdate",
                    "name": {
                        "en-GB": "Save"
                    },
                    "description": {},
                    "transitionTo": null,
                    "exitActions": null,
                    "color": "blue",
                    "groupId": "save",
                    "uiAction": "none",
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
                }, {
                    "id": "submit",
                    "name": {
                        "en-GB": "Re-submit"
                    },
                    "description": {
                        "en-GB": "Re-submit the entry for approval"
                    },
                    "transitionTo": "awaitingApproval",
                    "exitActions": [{
                            "invokeAction": "validateEntry"
                        }
                    ],
                    "color": "blue",
                    "groupId": "submitRevoke",
                    "uiAction": "navigateToEntryListing",
                    "parameters": [{
                            "id": "message",
                            "name": {
                                "en-GB": "Message"
                            },
                            "dataType": "string",
                            "dataFormat": null,
                            "description": {
                                "en-GB": "The message included with the entry re-submission"
                            },
                            "default": null,
                            "validations": {},
                            "editor": {
                                "id": "multiline",
                                "instructions": {
                                    "en-GB": "Include a message to let an approver understand the reasons for the re-submisson"
                                },
                                "properties": null
                            }
                        }
                    ]
                }
            ],
            "color": "red",
            "uiEditorView": "default"
        }, {
            "id": "versionComplete",
            "name": {
                "en-GB": ""
            },
            "entryActions": [],
            "events": [{
                    "id": "sysUpdate",
                    "name": {
                        "en-GB": "Save"
                    },
                    "description": {},
                    "transitionTo": "draft",
                    "exitActions": null,
                    "color": "blue",
                    "groupId": "save",
                    "uiAction": "none",
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
            "color": "green",
            "uiEditorView": "default"
        }
    ],
    "eventGroups": [{
            "id": "save",
            "name": {
                "en-GB": "Save"
            }
        }, {
            "id": "submitRevoke",
            "name": {
                "en-GB": "Submit / revoke"
            }
        }, {
            "id": "approveDecline",
            "name": {
                "en-GB": "Approve / decline"
            }
        }, {
            "id": "delete",
            "name": {
                "en-GB": "Delete"
            }
        }
    ],
    "isSystem": true,
    "version": {
        "createdBy": "",
        "created": "0001-01-01T00:00:00",
        "modifiedBy": "",
        "modified": "0001-01-01T00:00:00",
        "publishedBy": null,
        "published": null,
        "versionNo": null
    }
}
```
