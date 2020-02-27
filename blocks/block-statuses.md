# Block statuses

A block has a number of statuses

* [Workflow status](#workflow-status)
* [Deployment status](#deployment-status)
* [Running status](#running-status)

## Workflow status

These statuses describe the state the block has progressed to in its workflow stages.

| Name             | Description                                                                     |
| :--------------- | :------------------------------------------------------------------------------ |
| Created          | The block has just been pushed and has not yet started being discovered         |           
| Discovering      | The block discovery process is ongoing                                          |
| DiscoveryFailure | The block discovery process has failed                                          |
| Draft            | The block discovery process was successful and the block is now a draft version |
| Released         | The block has been released and its major version incremented                   |

## Deployment status

These statuses describe the deployment status that has been specified for a block.

| Name       | Description                                              |
|------------|----------------------------------------------------------|
| None       | The block is not ready                                   |
| Deployed   | The block is intended to be run                          |
| Live       | The block has been marked as live and publicly available |
| Deprecated | The block has been replaced with a newer version         |

## Running status

These statuses describe the current running status of the block.

| Name      | Description                                                        |
| :-------- | :----------------------------------------------------------------- |
| None      | The block has not been set to run                                  |
| Pending   | The block is intended to run and is currently being setup to do so |
| Starting  | The block is currently starting up                                 |
| Available | The block is running successfully                                  |
| Stopped   | The block was running but is no longer                             |
| Degraded  | The block is not running successfully in one or more instances     |
| Faulted   | The block is not running successfully in all instances             |