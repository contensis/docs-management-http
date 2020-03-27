---
description: API access token resource
---
# API acess token

API access token resource

## Properties

| Name        | Type        | Format               | Description                                             |
|-------------|-------------|----------------------|---------------------------------------------------------|
| id          | string      |                      | The access token identifier as a 128 bit GUID.          |
| name        | string      |                      | The access token name                                   |
| description | string      |                      | An optional description for the access token            |
| enabled     | boolean     |                      | A flag to enable or disable the access token            |
| version     | object      | [version](./version) | The version details for the proxy resource              |
| scopes      | string[] | {projectId}_{api}    | The list of project api scopes, e.g. *website_delivery* |
| createdBy   | string      |                      | The user id of who created the access token             |
| created     | string      | datetime             | The date and time the access token was created          |
| modifiedBy  | string      |                      | The user id of who last modified the access token       |
| modified    | string      | datetime             | The date and time the access token was last modified    |


## Remarks

An asterisk can be specified as the key for an endpoint to handle all languages excluding any endpoint explicitly declared with a language. If no asterisk-keyed endpoint is specified then only the languages provided will be proxied.  

If no host is provided for a URI that includes the domain, then the host header is automatically added on creation. 

## Example

```json
{
    "id": "8f3dad0f-9ac3-450f-a825-0457542c04c7",
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": true,
    "scopes": [
        "website_delivery",
        "website_management",
        "internal_delivery"
    ]
}
```