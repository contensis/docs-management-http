---
description: The date range object represents a start and end point in time.
---
# Date range

The date range object represents a start and end point in time.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :-- | :---------- |
| from | datetime | | The date and time the range starts. |
| to | datetime | | The date and time the range ends. |

## Validation

The *from* value cannot be greater than the *to* value.

## Example

```json
{
    "from": "2006-12-06T09:00:00",
    "to": "2009-09-10T09:00:00"
}
```
