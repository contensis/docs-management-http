---
description: Components are added to a content type as a field just like any other field, however the dataFormat of the field specifies the id of the component to add.
---

## Add a component to a content type

Components are added to a content type as a field just like any other field, however the dataFormat of the field specifies the id of the component to add.

For example if you have a component with an id of "movieRole" then the dataFormat value would be "component.movieRole".

### Example JSON

```json
"fields":[
    {  
        "id":"movieRole",
        "name": {  
            "en-GB":"Movie Role"
        },
        "dataType":"object",
        "dataFormat":"component.movieRole",
        "description": {  
            "en-GB":"The movie Role"
        }
    }
]
```

After a content type has been saved with a component field, all of the component's fields are added to a nested fields collection within the component field on the content type. A components' fields are read-only, and cannot be modified from the content type.
