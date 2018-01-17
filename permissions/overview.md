## Permissions overview

There are three system defined permissions that can be assigned, these are:

|||
|-|-|
|Permission | Description |
|sys.create|If a role is assigned this permission users in the role are then able to create entries of the given content type(s)|
|sys.delete|If a role is assigned this permission users in the role are then able to delete entries for the given content type(s)|
|sys.delete|If a role is assigned this permission users in the role are then able to update entries for the given content type(s)|
|||

The remaining permissions are based on the workflow that has been assigned, given a work flow is assigned with a state called awaitingApproval which has the following events; approve, decline and revoke. Then there will be three additional permissions which can be assigned; awaitingApproval.approve, awaitingApproval.decline and awaitingApproval.revoke. 

If a user has permission for events in a given workflow state they will not be able to invoke those events.
