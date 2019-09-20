---
description: .
---
# Block

TODO

## Properties

| Name                           | Type      | Format                                   | Description                            |
|:-------------------------------|:----------|:-----------------------------------------|:---------------------------------------|
| id                             | string    |                                          | The block identifier                   |
| projectId                      | string    |                                          | The project identifier                 |
| branches.id                    | string    |                                          | The id of the branch                   |
| branches.versions.versionNo    | string    | [versionNo](/model/version.md#versionNo) | The block version number               |
| branches.versions.runningState | string    |                                          | The running state of the block version |

## Block running states

| Name     | Description                                                         |
|:---------|:--------------------------------------------------------------------| 
| Faulted  | The block has stopped due to an error                               |
| Running  | The block is expected to be running and currently is                |
| Starting | The block is expected to be running and is currently starting       |
| Stopped  | The block is not expected to be running and is deliberately stopped |
| Stopping | The block is expected to be stopped and is currently stopping       |

## Remarks


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
                    "runningState": "Running"
                },
                {
                    "versionNo": "0.2",
                    "runningState": "Stopped"
                },
                {
                    "versionNo": "0.1",
                    "runningState": "Stopped"
                }

            ]
        },
        {
            "id": "feature-redesign-2019",
            "versions":[
                {
                    "versionNo": "0.3",
                    "runningState": "Starting"
                },
                {
                    "versionNo": "0.2",
                    "runningState": "Stopped"
                },
                {
                    "versionNo": "0.1",
                    "runningState": "Faulted"
                }
            ]
        }
    ]
}
```