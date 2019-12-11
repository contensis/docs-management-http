---
description: A node represents a location within the navigational structure of a website. A single entry can be assigned to a node, separating the responsibility of navigation management from content editing. The linking of nodes as parent-child relationships forms the hierarchical structure of a website, with a node having a single parent and (optionally) multiple child nodes.
---

# Node

A node represents a location within the navigational structure of a website. The linking of nodes as parent-child relationships forms the hierarchical structure of a website, with a node having a single parent and (optionally) multiple child nodes.

A single entry can be assigned to a node, separating the responsibility of navigation management from content editing.

## Properties

| Name                  | Type        | Format                                                          | Description                                                                                                                                                            |
|-----------------------|-------------|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                    | string      | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The node identifier as a 128 bit GUID.                                                                                                                                 |
| parentId              | string      | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The identifier of the parent node as a 128 bit GUID.                                                                                                                   |
| projectId             | string      |                                                                 | The friendly name given to the project.                                                                                                                                |
| displayName           | object      | [Localized value](/key-concepts/localization.md)                | The localised displayName of the node.                                                                                                                                 |
| slug                  | object      | [Localized value](/key-concepts/localization.md)                | The localised name of the node in slug format. Automatically created from the relevant title variation if not provided. Must be in slug format if provided as a value. |
| entryId               | string      | [GUID](https://docs.microsoft.com/en-us/dotnet/api/system.guid) | The identifier of the referenced entry as a 128 bit GUID.                                                                                                              |
| restrictedToLanguages | stringArray |                                                                 | An array of all the languages supported by the node.                                                                                                                   |
| childCount            | number      |                                                                 | The count of child nodes.                                                                                                                                              |
| isCanonical           | boolean     |                                                                 | 'true' if the node represents the canonical path for the associated entry; 'false' otherwise.                                                                          |
| includeInMenu         | boolean     |                                                                 | 'true' if the node should be included in menus; 'false' otherwise. Defaults to 'true'. Does not stop the node from being navigable.                                    |

## Example

```json
{
	"id": "baf2d873-6f65-4dbe-b3ad-b4d194c963b2",
	"parentId": "28107355-a43a-4b94-bc6c-28b6ac622258",
	"projectId": "movieDatabase",
	"displayName": {
		"en-GB": "Kelly's Heroes"
	},
	"slug": {
		"en-GB": "kellys-heroes"
	},
	"entryId": "88b9941c-59bb-4954-9a8e-8c8ac3a77f45",
	"restrictedToLanguages": ["en-GB", "fr-FR"],
	"childCount": 5,
	"isCanonical": true,
	"includeInMenu": true
}
```
