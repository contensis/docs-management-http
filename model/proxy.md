---
description: TODO
---
# Proxy

A proxy configuration

## Properties

### Proxy

| Name        | Type   | Format               | Description                                |
|-------------|--------|----------------------|--------------------------------------------|
| id          | string |                      | The proxy identifier as a 128 bit GUID.    |
| projectId   | string |                      | The project api identifier                 |
| name        | string |                      | The proxy name                             |
| description | string |                      | An optional description for the proxy      |
| endpoints   | object | [Proxy endpoint](#proxy-endpoint)             | Endpoint configurations keyed by language  |
| version     | object | [version](./version) | The version details for the proxy resource |


### Proxy endpoint

| Name    | Type   | Format | Description                                                     |
|---------|--------|--------|-----------------------------------------------------------------|
| uri     | string | URI    | The full URI to the server endpoint, which may include the path |
| headers | object |        | Header key-value pairs that should be added with each request   |

## Remarks

An asterisk can be specified as the key for an endpoint to handle all languages excluding any endpoint explicitly declared with a language. In no asterisk-keyed endpoint is specified then only the languages provided will be proxied.  

If no host is provided for a URI that includes the domain, then the host header is automatically added on creation. 

## Example

```json
{
    "id": "7622b5f7-e245-4226-9e64-3aeafa930eae",
    "projectId": "movieDb",
    "name": "Thrillers section",
    "description": "Proxies current website thrillers section",
    "endpoints": {
        "*": {
            "uri": "https://10.32.187.17:443/{language}/movies/thrillers",
            "headers": {
                "host": "www.moviedb.com",
            }
        },
        "fr-FR": {
            "uri": "https://www.moviedb.com/movies/le-thrillers",
            "headers": {
                "host": "www.moviedb.com" 
            }
        }
    },
    "version": {
        "versionNo": "2.0",
        "created": "2020-02-13T10:15:12.1973648+01:00",
        "createdBy": "t.durden",
        "modified": "2020-02-13T10:15:12.1973648+01:00",
        "modifiedBy": "t.durden",
        "published": "2020-02-13T10:15:12.1973648+01:00",
        "publishedBy": "t.durden"
    }
}
```