---
description: Updates an existing workflow definition.
---

# Update a workflow definition

Updates a workflow definition resource.

<span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}**

## Parameters

| Name | Parameter type | Type | Format | Description |
|:-|:-|:-|:-|:-|
| projectId | path | string |  | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console. |
| workflowDefinitionId | path | string |  | The workflow definition identifier. |

## Example request

```json
PUT: /api/management/projects/movieDb/workflow/definitions/approvalWorkflow

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
| 200              | Updated             | [Workflow Definition](/model/workflow-definition.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)       |
| 404              | NotFound            | [Error](/key-concepts/errors.md)       |
| 409              | NotLatestVersion    | [Error](/key-concepts/errors.md)       |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)       |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)       |

## Validations

| Type | Description |
|-|-|
| Id does not exist | The workflow definition must be unique for the project |
| Project does not exist | The content type must be unique for the project |

*TODO - Add validations*
