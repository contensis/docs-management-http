---
description: The version object contains the version status information for the current version of the resource.
---
# Version

The version object contains the version status information for the current version of the resource.

## Properties

| Name        | Type   | Format          | Description                                                |
|-------------|--------|-----------------|------------------------------------------------------------|
| createdBy   | string |                 | The user id of who created the resource.                   |
| created     | string | datetime        | The date and time the resource was created.                |
| modifiedBy  | string |                 | The user id of who last modified the resource.             |
| modified    | string | datetime        | The date and time the resource version was last modified.  |
| publishedBy | string |                 | The user id of who last published the resource.            |
| published   | string | datetime        | The date and time the resource version was last published. |
| versionNo   | string | {Major}.{Minor} | The version number of the resource.                        |


## VersionNo

The *versionNo* value follows a two-part version scheme:

> {Major}.{Minor}

The *minor* part is incremented on every successful update to the entry. The *major* part is incremented once the entry has been approved and subsequently published, which in turn resets the *minor* part to zero.


## Example

```json
{
    "version": {
        "createdBy": "s.derrickson",
        "created": "2016-10-12T09:29:18.5144641+01:00",
        "modifiedBy": "b.cumberbatch",
        "modified": "2016-10-13T10:15:12.1973648+01:00",
        "publishedBy": "b.cumberbatch",
        "published": "2016-10-13T10:15:12.1973648+01:00",
        "versionNo": "2.0"
    }
}
```
