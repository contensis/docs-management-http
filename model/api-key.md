---
description: API key resource
---
# API key

An API key resource contains the client credential details and access token required to use the Contensis APIs. Project and individual API access is controlled with specific scopes. 

## Properties

| Name               | Type     | Format                                 | Description                                                    |
|--------------------|----------|----------------------------------------|----------------------------------------------------------------|
| id                 | string   |                                        | The API key identifier as a 128 bit GUID                       |
| name               | string   |                                        | The API key name                                               |
| description        | string   |                                        | An optional description for the API key                        |
| enabled            | boolean  |                                        | A flag to enable or disable the API Key                        |
| oAuth              | object   |                                        | The OAuth client details                                       |
| oAuth.grantType    | string   |                                        | The security client grant type, default is 'clientCredentials' |
| oAuth.clientId     | string   |                                        | The read-only OAuth client id                                  |
| oAuth.clientSecret | string   |                                        | The read-only OAuth shared secret                              |
| scopes             | string[] | {api}_{projectId}                      | The list of project api scopes, e.g. *delivery_website*        |
| accessTokens       | object[] | [Access token](/model/access-token.md) | The access tokens created for the API key                      |
| createdBy          | string   |                                        | The user id of who created the API key                         |
| created            | string   | datetime                               | The date and time the API key was created                      |
| modifiedBy         | string   |                                        | The user id of who last modified the API key                   |
| modified           | string   | datetime                               | The date and time the API key was last modified                |


## Example

```json
{
    "id": "8f3dad0f-9ac3-450f-a825-0457542c04c7",
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": true,
    "oAuth":{
        "grantType": "clientCredentials",
        "clientId": "7823acca-8a7a-42c6-974c-aad1794c6e8c",
        "clientSecret": "09750005d532433f8b4963d849589748-09cf1d276bd44d979d5c5d0175ec5901-56712fd1283f4c64a7e4d7fbfc66693b" 
    },
    "accessTokens": [
        {
            "name": "default",
            "token": "3gNAeyXAqClzWd4XH8kL4zFgxskDntaNtPkVXBOXjFKs6Mx3",
        }
    ],
    "scopes": [
        "delivery_website",
        "management_website",
        "delivery_internal"
    ],
    "createdBy": "s.derrickson",
    "created": "2016-10-12T09:29:18.5144641+01:00",
    "modifiedBy": "b.cumberbatch",
    "modified": "2020-03-24T14:51:35.7048498Z"
}
```