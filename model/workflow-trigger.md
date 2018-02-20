# Workflow trigger

The workflow trigger model is used within workflow event invocation requests.

## Properties

| Name | Type | Format | Description |
| :------- | :--- | :----- | :---------- |
| language | string | | The language of the target entry variation |
| version | string | {Major}.{Minor} | The version number of the target entry variation |
| event | string | | The name of the workflow event to invoke |
| data | object |  | Data to include with the workflow event invocation |

## Example

This example shows a workflow trigger.

```json
{
    "language": "en-GB",
    "version": "2.3",
    "event": "draft.submit",
    "data": {
        "message": "Have updated the final paragrah"
    }
}
```