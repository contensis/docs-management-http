# Scopes

OAuth 2.0 scopes allow a developer to specify which resources their application can access. These are included as a space-separated list value, in the scope parameter when invoking an [authentication](/authentication.md) request.

| Scope name | Associated methods |
|:-|:-|
| Project_Read | [GET a single project](/key-concepts/get-project.md) |
| Project_Write | [Create a project](/key-concepts/get-project.md)<br />[Update a project]()|
| Project_Delete | [GET a single project](/key-concepts/get-project.md) |
| ContentType_Read | [GET a single content type](/key-concepts/get-contenttype.md) |
| Entry_Read | [GET a single entry](/key-concepts/get-entry.md)<br />[GET a list of all entries ](/key-concepts/list-entries.md#list-all-entries)<br />[GET a list of entries by content type](/key-concepts/list-entries-by-content-type.md) |



## Example request

```http
POST: https://cms-yourcontensis.com/authenticate/connect/token
Content-Type: application/x-www-form-urlencoded
Accept: application/json

grant_type=client_credentials&
client-id=bda30e56-4faf-412c-b460-6fce9342b162&
client-secret=1e2759cee76b4ae7947722be71cc33e1-56a63ae1361241fdab7c9ee90cc8a6b3-6dc4c02b8eda43d49de499ad5eef1160&
scope=Entry_Read ContentType_Read Project_Read
```
