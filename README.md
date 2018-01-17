# Contensis HTTP Management API

## Introduction

The Management API allows you to create and manage entries within Contensis. 
Our primary aim with this version of the API is to enable you to easily import/integrate content from other systems.

The API is a RESTful service to ensure maximum compatibility, delivering content as JSON and resource files (assets) as text or binary files. We currently provide a .NET client API wrapper to simplify using the API.

## Key concepts

### Projects

|||
|-|-|
| [Get a project](/projects/get-a-project.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/ |
| [Create a project](/projects/create-a-project.md) | <span class="label label--post">POST</span> /api/management/projects/ |
| [Update a project](/projects/update-a-project.md) | <span class="label label--post">PUT</span> /api/management/projects/**{projectId}**/ |
| [List projects](/projects/list-projects.md) | <span class="label label--get">GET</span> /api/management/projects/ |
| [Delete a project](/projects/delete-a-project.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/ |

<!-- ### Content Types

|||
|-|-|
| [Get a content type](/key-concepts/content-types.md#get-a-content-type) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}** |
| [Create a content type](/key-concepts/content-types.md#create-a-content-type) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/contenttypes/ |
| [Update a content type](/key-concepts/content-types.md#update-a-content-type) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}** |
| [Publish a content type](/key-concepts/content-types.md#publish-a-content-type) | <span class="label label--post">POST</span> /api/management/workflow/ |
| [List content types](/key-concepts/content-types.md#list-content-types) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/ |
| [Delete a content type](/key-concepts/content-types.md#delete-a-content-type) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/ | -->

### Entries

|||
|-|-|
| [Get an entry](/entries/get-an-entry.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/**{entryId}** |
| [Create an entry](/entries/create-an-entry.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/entries/ |
| [Update an entry variation](/entries/update-an-entry.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/entries/**{entryId}**
| [Publish an entry](/entries/publish-an-entry.md) | <span class="label label--put">PUT</span> /api/management/workflow/ |
| [List entries](/entries/list-entries.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/entries/ |
| [List entries by content type](/entries/list-entries-by-content-type.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/contenttypes/**{contentTypeId}**/entries/ |
| [Delete an entry](/entries/delete-an-entry.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**
| [Delete an entry variation](/entries/delete-an-entry-variation.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/entries/**{entryId}**/**{language}**/

### Roles

|||
|-|-|
| [Get a role](/roles/get-a-role.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}** |
| [Create a role](/roles/create-a-role.md) | <span class="label label--post">POST</span> /api/management/projects/**{projectId}**/security/roles/ |
| [Update a role](/roles/update-a-role.md) | <span class="label label--put">PUT</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}** 
| [List roles](/roles/list-roles.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/roles/ |
| [Delete a role](/roles/delete-a-role.md) | <span class="label label--delete">DELETE</span> /api/management/projects/**{projectId}**/security/roles/**{roleId}** 

### Permissions
|||
|-|-|
| [Overview](/permissions/overview.md) | |
| [Get permissions for a resource](/permissions/get-permissions-for-a-resource.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/**{resourceType}**/**{resourceId?}**?userId=**{userId}** |
| [Get authorization for a resource action](/permissions/get-authorization-for-a-resource-action.md) | <span class="label label--get">GET</span> /api/management/projects/**{projectId}**/security/permissions/**{resourceType}**/**{resourceId?}**/actions/**{action}**?userId=**{userId}** |
