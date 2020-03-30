---
description: API access token resource
---
# API acess token

API access token resource

## Properties

| Name        | Type     | Format               | Description                                             |
|-------------|----------|----------------------|---------------------------------------------------------|
| id          | string   |                      | The access token identifier as a 128 bit GUID.          |
| name        | string   |                      | The access token name                                   |
| description | string   |                      | An optional description for the access token            |
| token       | string   |                      | The generated access token value                        |
| enabled     | boolean  |                      | A flag to enable or disable the access token            |
| version     | object   | [version](./version) | The version details for the proxy resource              |
| scopes      | string[] | {projectId}_{api}    | The list of project api scopes, e.g. *website_delivery* |
| createdBy   | string   |                      | The user id of who created the access token             |
| created     | string   | datetime             | The date and time the access token was created          |
| modifiedBy  | string   |                      | The user id of who last modified the access token       |
| modified    | string   | datetime             | The date and time the access token was last modified    |


## Remarks



## Example

```json
{
    "id": "8f3dad0f-9ac3-450f-a825-0457542c04c7",
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "token": "3gNAeyXAqClzWd4XH8kL4zFgxskDntaNtPkVXBOXjFKs6Mx3",
    "enabled": true,
    "scopes": [
        "website_delivery",
        "website_management",
        "internal_delivery"
    ]
}
```