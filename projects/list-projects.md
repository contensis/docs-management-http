## List projects

Returns a list of the project resources for a Contensis instance.

<span class="label label--get">GET</span> /api/management/projects/

### Example request

```http
GET: /api/management/projects/
```


### Response messages

| HTTP status code | Reason | Response model |
|:-|:-|:-|
| 200 | Success | [Project [...]](/model/project.md) |
| 401 | Unauthorized | [Error](/key-concepts/errors.md) |
| 404 | NotFound | [Error](/key-concepts/errors.md) |
| 500 | InternalServerError | [Error](/key-concepts/errors.md) |