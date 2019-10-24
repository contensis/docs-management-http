---
description: The block resource provides an overview of the versions of a block
---
# Block

The block resource provides details about each pushed version of a block. Block versions relate to a GIT branch, with the default branch being the 'master' branch.

## Properties

| Name                                | Type     | Format                                            | Description                                 |
|:------------------------------------|:---------|:--------------------------------------------------|:--------------------------------------------|
| id                                  | string   |                                                   | The block identifier                        |
| projectId                           | string   |                                                   | The project identifier                      |
| branches                            | object[] |                                                   | Array of branches                           |
| branches.id                         | string   |                                                   | The id of the branch                        |
| branches.versions                   | object[] |                                                   | Array of Block version details              |
| branches.versions.versionNo         | string   | [versionNo](/model/version.md#versionNo)          | The block version number                    |
| branches.versions.status.broken     | boolean  |                                                   | Whether the block has been marked as broken |
| branches.versions.status.deployment | string   | [Deployment status](/blocks/deployment-status.md) | The block deployment status                 |
| branches.versions.status.running    | string   | [Running status](/blocks/running-status.md)       | The block running status                    |
| branches.versions.status.workflow   | string   | [Workflow status](/blocks/workflow-status.md)     | The block workflow status                   |

## Example response

```json
{ 
    "id": "movie-listing",
    "projectId": "movieDb",
    "branches": [
        {
            "id": "master",
            "versions": [                
                {
                    "versionNo": "1.1",
                    "status": {
                        "broken": false, 
                        "deployment": "Deployed",      
                        "running": "Pending",
                        "workflow": "Draft",
                    }
                },
                {
                    "versionNo": "1.0",
                    "status": {
                        "broken": false, 
                        "deployment": "Deployed",      
                        "running": "Available",
                        "workflow": "Released",
                    }    
                },
                {
                    "versionNo": "0.2",
                    "status": {
                        "broken": false, 
                        "deployment": "Deprecated",      
                        "running": "Stopped",
                        "workflow": "Draft",
                    }    
                },
                {
                    "versionNo": "0.1",
                    "status": {
                        "broken": true, 
                        "deployment": "Deprecated",      
                        "running": "Stopped",
                        "workflow": "Draft",
                    }  
                }

            ]
        },
        {
            "id": "feature-redesign-2019",
            "versions":[
                {
                    "versionNo": "0.3",
                    "status": {
                        "broken": false, 
                        "deployment": "Deployed",      
                        "running": "None",
                        "workflow": "Created",
                    }  
                },
                {
                    "versionNo": "0.2",
                    "status": {
                        "broken": false, 
                        "deployment": "Deprecated",      
                        "running": "Stopped",
                        "workflow": "Draft",
                    } 
                },
                {
                    "versionNo": "0.1",
                    "status": {
                        "broken": false, 
                        "deployment": "Deprecated",      
                        "running": "Stopped",
                        "workflow": "Draft",
                    } 
                }
            ]
        }
    ]
}
```