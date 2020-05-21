---
description: An action which is performed on an entry when it enters or leaves a workflow state.
---
# Workflow actions

An action which is performed on an entry when it enters or leaves a workflow state. Entry actions are specified in the workflow [state](state) and exit actions are specified in the workflow state [event](event).

## Supported actions

The following list contains the actions that are currently supported:

| Exit action | Description |
| :---------- | :-------- | 
| validateEntry | Causes the entry's fields to be validated. |
| publishEntry | Causes the entry to be published. |
| updateEntry | Causes the entry to be updated and any changes to be saved. |

## Examples

The permitted actions are:

```json
{
    "invokeAction": "validateEntry"
}
```

```json
{
    "invokeAction": "publishEntry"
}
```

```json
{
    "invokeAction": "updateEntry"
}
```
