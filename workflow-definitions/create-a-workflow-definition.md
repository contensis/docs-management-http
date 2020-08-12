---
description: Creates a new workflow definition resource.
---
# Create a workflow definition

Creates a new workflow definition resource.

<span class="label label--post">POST</span> /api/management/projects/**{projectId}**/workflow/definitions/

*N.B.* A custom workflow definition must be [published](/workflow-definitions/invoking-workflow.md) before it can be assigned to a content type.

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |

## Example request

```json
POST: /api/management/projects/movieDb/workflow/definitions/

{
    "id": "approvalWorkflow",
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
    ]
}
```

## Response message

| HTTP status code | Reason              | Response model                         |
|:-----------------|:--------------------|:---------------------------------------|
| 201              | Created             | [Workflow Definition](/model/workflow-definition.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 404              | NotFound            | [Error](/key-concepts/errors.md)       |
| 409              | Conflict            | [Error](/key-concepts/errors.md)       |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |

## Validations

| Type | Description |
|-|-|
| Project does not exist | A project must exist to be able to create a workflow definition. |
| Id missing | The workflow definition id must be defined. |
| Non-unique id | The workflow definition id must be unique for the project. |
| Maximum id length | The workflow definition id cannot be more than 50 characters long. |
| Invalid id | The workflow definition id must begin with a letter and only contain alphanumeric characters. |
| Name missing | The workflow definition name must be defined. |

## Validations for [states](/model/workflow-definitions/state.md)

| Type | Description |
|-|-|
| State id missing | The state id must be defined. |
| State id non-unique | State ids must be unique for the workflow definition. |
| State id maximum length | A state id cannot be more than 50 characters long. |
| State id invalid | A state id must begin with a letter and only contain alphanumeric characters, and no spaces. |
| State name missing | The state name must be defined. |

## Validations for [events](/model/workflow-definitions/event.md)

| Type | Description |
|-|-|
| Event id missing | The event id must be defined. |
| Event id non-unique | Event ids must be unique for the parent state. |
| Event id maximum length | An event id cannot be more than 50 characters long. |
| Event  id invalid | An event id must begin with a letter and only contain alphanumeric characters, and no spaces. |
| Event name missing | The event name must be defined. |
| Transition to state invalid | The transition to state must be a valid state id. |
| Group id missing | The group id must be defined. |
| Group id invalid | The group id must be a valid event group id. |
| Exit action invalid | If defined, the exit action must be a valid [action](/model/workflow-definitions/action.md). |


## Validations for [parameters](/model/workflow-definitions/parameter.md)

| Type | Description |
|-|-|
| Parameter id missing | The parameter id must be defined. |
| Parameter id non-unique | Parameter ids must be unique for the parent event. |
| Parameter id maximum length | A parameter id cannot be more than 50 characters long. |
| Parameter id invalid | A parameter id must begin with a letter and only contain alphanumeric characters, and no spaces. |
| Parameter name missing | The parameter name must be defined. |
| Validation invalid | If defined, the validation must be a valid [validation](/model/workflow-definitions/validation.md). |
| Editor invalid | If defined, the editor must be a valid [editor](/model/workflow-definitions/editor.md). |

## Validations for [event groups](/model/workflow-definitions/event-group.md)

| Type | Description |
|-|-|
| Event group id missing | The event group id must be defined. |
| Event group id non-unique | Event group ids must be unique for the workflow definition. |
| Event group id maximum length | An event group id cannot be more than 50 characters long. |
| Event group id invalid | An event group id must begin with a letter and only contain alphanumeric characters, and no spaces. |
| Event group name missing | The event group name must be defined. |
