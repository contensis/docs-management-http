# Scopes

OAuth 2.0 scopes allow a developer to specify which resources their application can access. These are included as a space-separated list value, in the scope parameter when invoking an [authentication](/security/authentication.md) request.

| Scope name | Associated methods |
|:-|:-|
| Project_Read | [Get a project](/key-concepts/projects.md#get-a-project) |
| Entry_Read | [Get a entry](/key-concepts/entries.md#get-an-entry)<br />[List entries](/key-concepts/entries.md#list-entries)<br />[List entries by content type](/key-concepts/entries.md#list-entries-by-content-type) |
|Entry_Write|[Create an entry](/key-concepts/entries.md#create-an-entry)<br />[Update an entry](/key-concepts/entries.md#update-an-entry) <br /> [Publish an entry](/key-concepts/entries.md#publish-an-entry) |
|Entry_Delete|[Delete an entry](/key-concepts/entries.md#delete-an-entry)|



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
