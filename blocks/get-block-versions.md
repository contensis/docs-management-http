---
description: 
---
# Get block versions


<span class="label label--get">GET</span> /api/management/projects/**{projectId}**/blocks/movie-listing/versions

## Parameters

| Name      | Parameter type | Type   | Format | Description                                                                                            |
| :-------- | :------------- | :----- | :----- | :----------------------------------------------------------------------------------------------------- |
| projectId | path           | string |        | The project identifier, e.g. "movieDb". Found in the project overview screen of the management console |

### Example response

```json
{
    "versions":[
        {
            "versionNo": "3.2",
            "status": "Discovering"     
        },
        {
            "versionNo": "3.1",
            "status": "Latest"     
        },
        {
            "versionNo": "3.0",
            "status": "Deployed" 
        },
        {
            "versionNo": "2.7",
            "status": "Dead"       
        },
        {
            "versionNo": "2.0",
            "status": "Dead"           
        },
        {
            "versionNo": "1.4",
            "status": "Dead"             
        },
        {
            "versionNo": "1.0",
            "status": "Broken"    
        },
        {
            "versionNo": "0.1",
            "status": "Dead"            
        }
    ]
}
```




### Response message

| HTTP status code | Reason              | Response model                   |
| :--------------- | :------------------ | :------------------------------- |
| 200              | OK                  | Block versions                   |
| 401              | Unauthorized        | [Error](/key-concepts/errors.md) |
| 404              | NotFound            | [Error](/key-concepts/errors.md) |
| 422              | ValidationError     | [Error](/key-concepts/errors.md) |
| 500              | InternalServerError | [Error](/key-concepts/errors.md) |

### Validations