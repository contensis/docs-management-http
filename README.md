# Contensis HTTP Management API

## Introduction

The Management API allows you to create and manage entries within Contensis.
Our primary aim with this version of the API is to enable you to easily import/integrate content from other systems.

The API is a RESTful service to ensure maximum compatibility, delivering content as JSON and resource files (assets) as text or binary files. The life-cycle of  [content is controlled by workflow](/key-concepts/workflow.md) which can be controlled by invoking permissiod events. We currently provide a [.NET](https://developer.zengenti.com/contensis/api/management/dotnet/) client API wrapper to simplify using the API.

## Key concepts

### Projects

|||
|-|-|
| [Get a project](/projects/get-a-project.md)       | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/       |
| [Create a project](/projects/create-a-project.md) | <span class="label label--post">POST</span> /api/management/projects/                     |
| [Update a project](/projects/update-a-project.md) | <span class="label label--post">PUT</span> /api/management/projects/**{projectId}**/      |
| [List projects](/projects/list-projects.md)       | <span class="label label--get">GET</span> /api/management/projects/                       |
| [Delete a project](/projects/delete-a-project.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/ |

### Content Types
|||
|-|-|
| [Get a content type](/content-types/get-a-content-type.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}** |
| [Create a content type](/content-types/create-a-content-type.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/contenttypes/ |
| [Update a content type](/content-types/update-a-content-type.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}** |
| [List content types](/content-types/list-content-types.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/ |
| [Delete a content type](/content-types/delete-a-content-type.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}** |
| [Publish a content type](/content-types/invoking-workflow.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/workflow/events/ |

### Components
|||
|-|-|
| [Get a component](/components/get-a-component.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/components/**{componentId}** |
| [Create a component](/components/create-a-component.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/components/ |
| [Update a component](/components/update-a-component.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/components/**{componentId}** |
| [Add a component to a content type](/components/add-a-component-to-a-content-type.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}** |
| [List components](/components/list-components.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/components/ |
| [Delete a component](/components/delete-a-component.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/components/**{componentId}** |
| [Publish a component](/components/invoking-workflow.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/components/**{componentId}**/workflow/events/ |

### Entries

|||
|-|-|
| [Get an entry](/entries/get-an-entry.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/**{entryId}** |
| [Create an entry](/entries/create-an-entry.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/ |
| [Update an entry variation](/entries/update-an-entry.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/entries/**{entryId}**
| [List entries](/entries/list-entries.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/ |
| [List entries by content type](/entries/list-entries-by-content-type.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/entries/ |
| [Delete an entry](/entries/delete-an-entry.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**
| [Delete an entry variation](/entries/delete-an-entry.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**?language=**comma separated list of languages**
| [Invoke a workflow event](/entries/invoking-workflow.md) <br> [Unpublish an entry](/entries/unpublish-an-entry.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/workflow/events/

### Nodes

|                                                         |                                                                                                                            |
|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| [Get the root node](/nodes/get-root-node.md)            | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/root/                             |
| [Get a node](/nodes/get-a-node.md)                      | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**                      |
| [Get nodes by entry id](/nodes/get-nodes-by-entryid.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/?entryId=**{entryId}**            |
| [Get a node's children](/nodes/get-nodes-children.md)   | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/nodes/**{parentNodeId}**/children       |
| [Create a node](/nodes/create-a-node.md)                | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/nodes/**{parentNodeId}**/children     |
| [Update a node](/nodes/update-a-node.md)                | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**/                     |
| [Move a node](/nodes/move-a-node.md)                    | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**/                     |
| [Delete a node](/nodes/delete-a-node.md)                | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/nodes/**{nodeId}**/               |
| [Order nodes](/nodes/order-nodes.md)                    | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/nodes/**{parentNodeId}**/children/order |

### Roles
|||
|-|-|
| [Get a role](/roles/get-a-role.md)       | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}**       |
| [Create a role](/roles/create-a-role.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/security/roles/                 |
| [Update a role](/roles/update-a-role.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}**       |
| [List roles](/roles/list-roles.md)       | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/roles/                   |
| [Delete a role](/roles/delete-a-role.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}** |

### Permissions
|||
|-|-|
| [Overview](/permissions/overview.md) | |
| [Get permissions for a resource](/permissions/get-permissions-for-a-resource.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/**{resourceType}**/**{resourceId?}**?userId=**{userId}** |
| [Get authorization for a resource action](/permissions/get-authorization-for-a-resource-action.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/**{resourceType}**/**{resourceId?}**/actions/**{action}**?userId=**{userId}** |
| [Get permissions for webhook subscriptions](/permissions/get-permissions-for-webhook-subscriptions.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/webhookSubscriptions?userId=**{userId}** |
| [Get authorization for a webhook subscription action](/permissions/get-authorization-for-a-webhook-subscription-action.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/webhookSubscriptions/actions/**{action}**?userId=**{userId}** |

### Workflow definitions
|||
|-|-|
|[Get a workflow definition](/workflow-definitions/get-a-workflow-definition.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}** |
|[Create a workflow definition](/workflow-definitions/create-a-workflow-definition.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/workflow/definitions/ |
|[Update a workflow definition](/workflow-definitions/update-a-workflow-definition.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}** |
|[List workflow definitions](/workflow-definitions/list-workflow-definition.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/workflow/definitions/ |
|[Delete a workflow definition](/workflow-definitions/delete-a-workflow-definition.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}** |
|[Publish a workflow definition](/workflow-definitions/invoking-workflow.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/workflow/definitions/**{workflowDefinitionId}**/workflow/events|


