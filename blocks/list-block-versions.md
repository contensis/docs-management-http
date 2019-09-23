---
description: 
---
# List block versions

<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks/**{blockId}**/**{branchId}**/versions

## Parameters

| Name          | Parameter type | Type   | Format | Description                                                                                            |
| :--------     | :------------- | :----- | :----- | :----------------------------------------------------------------------------------------------------- |
| projectId     | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |
| blockId       | path           | string |        | The block identifier                                                                                   |
| branchId      | path           | string |        | The branch identifier                                                                                  |

### Example request

```http
Accept: application/json
GET: /api/management/projects/movieDb/blocks/movie-listing/master/versions
```

## Example response

```json
{ 
    "id": "movie-listing",
    "projectId": "movieDb",
    "branches": [
        {
            "id": "master",
            "versions":[                
                {
                    "versionNo": "1.1",
                    "runningState": "Running",                    
                },
                {
                    "versionNo": "1.0",
                    "status": "Live"
                }
            ]
        },
        {
            "id": "feature-redesign-2019",
            "versions":[
                {
                    "versionNo": "0.3",
                    "status": "Available"
                },
                {
                    "versionNo": "0.2",
                    "status": "Superseded"
                },
                {
                    "versionNo": "0.1",
                    "status": "Superseded"
                }
            ]
        }
    ]
}
```

### Response message

| HTTP status code | Reason              | Response model                            |
| :--------------- | :------------------ | :---------------------------------------- |
| 200              | Success             | [PagedList&lt;Block&gt;](/model/block.md) |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md)          |
| 404              | NotFound            | [Error](/key-concepts/errors.md)          |
| 422              | ValidationError     | [Error](/key-concepts/errors.md)          |
| 500              | InternalServerError | [Error](/key-concepts/errors.md)          |

### Validations