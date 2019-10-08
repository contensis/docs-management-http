---
description: Projects offer a way of grouping related content types, entries and assets.
---
# Projects

Projects offer a way of grouping related content types, entries and assets. Typically a project would represent a single application such as a website, intranet or mobile application.

Projects are a licensed feature and the number you can create will depend on which license you have purchased.


## Get a project

Gets an existing project by the project id.

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**

### Example request

```http
GET: /api/management/projects/movieDb/
```

### Response messages

| HTTP status code | Reason              | Response model                   |
|:-----------------|:--------------------|:---------------------------------|
| 200              | Success             | [Project](/model/project.md)     |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |
