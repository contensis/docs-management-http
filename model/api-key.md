---
description: API key resource
---
# API key

An API key resource contains the client credential details and access token required to use the Contensis APIs. Project and individual API access is controlled with specific scopes. 

## Properties

| Name        | Type     | Format            | Description                                             |
|-------------|----------|-------------------|---------------------------------------------------------|
| id          | string   |                   | The API key identifier as a 128 bit GUID                |
| name        | string   |                   | The API key name                                        |
| description | string   |                   | An optional description for the API key                 |
| enabled     | boolean  |                   | A flag to enable or disable the API Key                 |
| flows       | object[] |                   | The supported flows for the API key                     |
| scopes      | string[] | {api}_{projectId} | The list of project api scopes, e.g. *delivery_website* |
| createdBy   | string   |                   | The user id of who created the API key                  |
| created     | string   | datetime          | The date and time the API key was created               |
| modifiedBy  | string   |                   | The user id of who last modified the API key            |
| modified    | string   | datetime          | The date and time the API key was last modified         |

## Remarks

When a new API key is created, both a `clientCredentials` and `accessToken` flow are created automatically.


## Example

```json
{
    "id": "8f3dad0f-9ac3-450f-a825-0457542c04c7",
    "name": "Main website",
    "description": "Allows read/write for website project and also access to internal for meeting information",
    "enabled": true,
    "flows":[
        {
            "id": "4946173e-3610-4ce6-8b68-f20338ac0070",
            "grantType": "clientCredential",
            "clientId": "mainWebsite",
            "clientSecret": "09750005d532433f8b4963d84958974809cf1d276bd44d979d5c5d0175ec590156712fd1283f4c64a7e4d7fbfc66693b" 
        },
        {
            "id": "f23b54ba-1796-49cc-90eb-2159c66e1f8a",
            "grantType": "accessToken",
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