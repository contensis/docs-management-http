# Block workflow status

These statuses describe the state the block has progressed to in its workflow stages.

| Name             | Description                                                                     |
| :--------------- | :------------------------------------------------------------------------------ |
| Created          | The block has just been pushed and has not yet started discovering              |           
| Discovering      | The block discovery process is ongoing                                          |
| DiscoveryFailure | The block discovery process has failed                                          |
| Draft            | The block discovery process was successful and the block is now a draft version |
| Released         | The block has been released and its major version incremented                   |

