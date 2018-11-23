---
description: A node represents a location within the navigational structure of a website. The linking of nodes as parent-child relationships forms the hierarchical structure of a website, with a node having a single parent and (optionally) multiple child nodes.

A single entry can be assigned to a node, separating the responsibility of navigation management from content editing.
---

# Node

A node represents a location within the navigational structure of a website. The linking of nodes as parent-child relationships forms the hierarchical structure of a website, with a node having a single parent and (optionally) multiple child nodes.

A single entry can be assigned to a node, separating the responsibility of navigation management from content editing.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| id | string | GUID | The node identifier as a 128 bit GUID. |
| parentId | string | GUID | The identifier of the parent node as a 128 bit GUID. |
| projectId | string |  | The friendly name given to the project. |
| name | object | [Localized value](/key-concepts/localization.md) | The localised name of the node. |
| entryId | string | GUID | The identifier of the referenced entry as a 128 bit GUID. |
| availableLanguages | string [...] |  | An array of all the languages supported by the node. |
| hasChildren | boolean | | 'True' if the node has any descendants; 'false' otherwise. |

## Example

```json
{
	"id": "baf2d873-6f65-4dbe-b3ad-b4d194c963b2",
	"parentId": "28107355-a43a-4b94-bc6c-28b6ac622258",
	"projectId": "movieDatabase",
	"name": {
		"en-GB": "kellysHeroes"
	},
	"entryId": "88b9941c-59bb-4954-9a8e-8c8ac3a77f45",
	"availableLanguages": ["en-GB", "fr-FR"],
	"hasChildren": false
}
```
