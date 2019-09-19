---
description: .
---
# Block Action

TODO

## Properties

| Name             | Type   | Format | Description                                      |
|:-----------------|:-------|:-------|:-------------------------------------------------|
| type             | string |        | The block action type                       |
| projectId        | string |        | The project identifier                           |


## Block Actions

| Name             | Description                                                       |
|:-----------------|:------------------------------------------------------------------|
| Release          | Releases the block version                                   |
| Rollback         | Rolls the block version back to a specified previous version |
| MarkAsBroken     | Marks the specified block version as broken                  |

## Remarks

## Example

```json
{
    "type": "rollback",
    "data": {
        "version": "2.0"
    }
}
```