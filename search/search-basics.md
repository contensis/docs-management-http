---
description: A query tree structure, along with order and paging specifiers, allows a search to be performed against indexed documents held in ElasticSearch. 
---
# Search

A query tree structure, along with order and paging specifiers, allows a search to be performed against indexed documents held in ElasticSearch. The query API allows any required sub-query structure to be defined and a comprehensive selection of Operators enable individual field level evaluation.

* [Queries](#queries)
* [Location searches](#location-searches)
* [Sub-queries](#sub-queries)
* [Ordering](#ordering)
* [Paging](#paging)
* [Weighting](#weighting)
* [Complete example](#complete-example)
* [HTTP GET queries](#http-get-queries)

## Queries

This example demonstrates a simple search using HTTP POST.

```json
POST: /api/management/projects/{projectId}/entries/search

{
    "where": [
        {
            "field": "title",
            "contains": "Batman"
        },
        {
            "field": "runtime",
            "greaterThan": 200
        }
    ]
}
```

Searches can also be carried out using [HTTP GET queries](#http-get-queries).

## Location searches

Search for locations within a radius of a specified location.

### Supported distance units

| Unit          | Search value                   |
|---------------|--------------------------------|
| Mile          | `mi` or `miles`                |
| Yard          | `yd` or `yards`                |
| Feet          | `ft` or `feet`                 |
| Inch          | `in` or `inch`                 |
| Kilometer     | `km` or `kilometers`           |
| Meter         | `m` or `meters`                |
| Centimeter    | `cm` or `centimeters`          |
| Millimeter    | `mm` or `millimeters`          |
| Nautical mile | `NM`, `nmi` or `nauticalmiles` |

### Example

Find all entries which have a location within 10.5 miles of Ludlow Castle's location.
Append the search value at the end of the distance specified, so for example "10.5mi" or "10.5miles".

```json
{
    "where": [{
        "field": "location",
        "distanceWithin": {
            "lat": "52.36700505",
            "lon": "-2.72304296",
            "distance": "10.5mi"
        }
    }]
}
```

When searching for a location field, you can also [order the results by distance](#ordering-by-distance).

## Sub-queries

A sub-query is a query within another query that is used as a condition to further restrict the results. Effectively they are defined by an explicit nesting of [logical operators](query-operators.md#logical-operators).

This example demonstrates a simple search with a sub-query:

```json
{
    "where": [
        {
            "field": "title",
            "contains": "Batman"
        },
        {
            "or": [
                {
                    "field": "releaseDate",
                    "greaterThan": 1960
                },
                {
                    "field": "tagline",
                    "contains": "gotham"
                }
            ]
        }
    ]
}
```

## Ordering

Results can be ordered by one or more fields in an ascending or descending direction. Order clauses are prioritised in the order that they are added. By default, if no order clauses are specified then the entry results are ordered by the EntryTitle in an ascending direction.

### Ascending order

Order by *releaseDate* in an ascending direction.

```json
{
    "orderBy": [{
        "asc": "releaseDate"
    }],
}
```

### Descending order

Order by *releaseDate* in a descending direction.

```json
{
    "orderBy": [{
        "desc": "releaseDate"
    }],
}
```

## Paging

Paging allows the number of results to be restricted to a defined count so that the results are easier to handle and ensures a response is returned quickly.

The page number can also be specified to allow which set of results is to be returned. The page size is limited to a maximum of 10,000 however this is not recommended.

```json
{
    "pageSize": 50,
    "pageIndex": 1
}
```
## Specifying fields

### System fields

System fields such as id, contentTypeId, projectId, versionNo etc. are under the *sys* object and can be accessed using a dot notation, e.g. sys.id, sys.contentTypeId, sys.projectId, sys.version.versionNo.

The *entryTitle* and *entryDescription* fields are dynamic values, determined by the *EntryTitleField* and *EntryDescriptionField* values in the content type.

### Data fields

Fields defined in the content type for the entry can be accessed by their API id.

### All fields

All fields can be searched by specifying an asterisk (*) in the field id. Note, the only supported operator is FreeText.

#### Example

```json
POST: /api/delivery/projects/{projectId}/entries/search
{
    "where": [
        {
            "field": "*",
            "equalTo": "Interstellar"
        }
    ]
}
```

### Array fields

### Array fields

Searching on array fields is the same as searching on a child property of a field, you just use the dot notation. All operators support searching across array fields.

#### Example array field search

This example searches for a quote source of "Bruce Willis" within a quote array field called movieQuote.

```json
POST: /api/management/projects/{projectId}/entries/search
{
    "where": [
        {
            "field": "movieQuote.source",
            "equalTo": "Bruce Willis"
        }
    ]
}
```

## Ordering by distance

When [searching by location](#location-searches), to return the search results according to the distance of the location field in each entry from the distance specified in the distanceWithin search, add the location field to the [orderBy](#ordering) clause, e.g.

```json
{
    "where": [{
        "field": "location",
        "distanceWithin": {
            "lat": "52.36700505",
            "lon": "-2.72304296",
            "distance": "10.5mi"
        }
    }],
    "orderBy": [{
        "asc": "location"
    }]
}
```

## Complete example

The following example combines the ordering, paging and weighting concepts.

```json
POST: /api/management/projects/{projectId}/entries/search
{
    "where": [
        {
            "field": "title",
            "contains": "Batman",
            "weight": 100
        },
        {
            "field": "synopsis",
            "freeText": "gotham",
            "weight": 30
        },
        {
            "field": "runtime",
            "greaterThan": 200
        }
    ],
    "orderBy": [
        {
            "desc": "releaseDate"
        }
    ],
    "pageIndex": 1,
    "pageSize": 50
}
```

## HTTP GET queries

Searches can also be carried out using an HTTP GET query, with the JSON for the individual sections of the query (*where*, *orderBy*, *pageSize*, *pageIndex*) specified as querystring parameters.

This example demonstrates a simple search using HTTP GET:

```json
GET: /api/management/projects/{projectId}/entries/search?where=[{"field":"title","contains":"Batman"},{"field":"runtime","greaterThan":200}]
```

This example demonstrates a more complex search using all the search options:

```json
GET: /api/management/projects/{projectId}/entries/search?where=[{"field":"title","contains":"Batman"},{"field":"runtime","greaterThan":200}]&orderBy=[{"asc":"title"}]&pageSize=10&pageIndex=0
```

N.B. The 'where' value of the querystring parameters will need to be URL encoded, this has not been done in the above examples for clarity. When URL encoded the examples look like this:

```json
GET: /api/management/projects/{projectId}/entries/search?where=%5B%7B%22field%22%3A%22title%22%2C%22contains%22%3A%22Batman%22%7D%2C%7B%22field%22%3A%22runtime%22%2C%22greaterThan%22%3A200%7D%5D
```

```json
GET: /api/management/projects/{projectId}/entries/search?where=%5B%7B%22field%22%3A%22title%22%2C%22contains%22%3A%22Batman%22%7D%2C%7B%22field%22%3A%22runtime%22%2C%22greaterThan%22%3A200%7D%5D%26orderBy%3D%5B%7B%22asc%22%3A%22title%22%7D%5D&pageSize=10&pageIndex=0
```
