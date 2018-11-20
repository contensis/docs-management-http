---
description: An AssetFile type is used for the creation or update of an asset.
---
# AssetFile

An AssetFile type is used for the creation or update of an asset. The type is always used as a [entry](/model/entry.md) field called 'sysAssetFile'.

## Properties

| Name | Type | Format | Description |
| :--- | :--- | :----- | :---------- |
| fileId | string | GUID | The file reference returned from an [asset file upload](/assets/upload-asset-file.md) |
| filename | string || An optional parameter to override the name of the file |
| parentNodePath | string | Forward-slash separated | The path to the parent node under which the asset should be created |

## Example

```json
{
    "sysAssetFile": {
        "fileId": "69ee6d40-32fd-452a-981b-f94abffdecc9.jpg",
        "filename": "batman-returns.jpg",
        "parentNodePath": "/uploads/movie-posters"
    }
}
```