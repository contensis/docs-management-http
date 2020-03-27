# Query operators

- [And](#and)
- [Or](#or)
- [Not](#not)
- [Between](#between)
- [Contains](#contains)
- [EndsWith](#endswith)
- [EqualTo](#equalto)
- [Exists](#exists)
- [FreeText](#freetext)
- [GreaterThan](#greaterthan)
- [GreaterThanOrEqualTo](#greaterthanorequalto)
- [In](#in)
- [LessThan](#lessthan)
- [LessThanOrEqualTo](#lessthanorequalto)
- [StartsWith](#startswith)
- [DistanceWithin](#distancewithin)


## Logical operators

### And
This would return any document where *first* is *1* AND *second* is *2*.

```json
{
    "where": [{
        "and": [{
            "field": "first",
            "equalTo": 1
        }, {
            "field": "second",
            "equalTo": 2
        }]
    }]
}
```

The *And* operator is the default logical operator and is not required to be specified explicitly.

```json
{
    "where": [{
        "field": "first",
        "equalTo": 1
    }, {
        "field": "second",
        "equalTo": 2
    }]
}
```



### Or
The example would return any document where *first* is *1* OR *second* is *2*.

```json
{
    "where": [{
        "or": [{
            "field": "first",
            "equalTo": 1
        }, {
            "field": "second",
            "equalTo": 2
        }]
    }]
}
```



### Not
The *not* expects an inner operator so in the example any document where *first* is NOT equal to *7* would be returned.


```json
{
    "where": [{
        "not": {
            "field": "first",
            "equalTo": 7
        }
    }]
}
```



## Relational & equality operators

### Between
In this example, if our field is between *18* and *45* inclusive it would match.

```json
{
    "where": [{
        "field": "age",
        "between": [18, 45]
    }]
}
```



### Contains
This would match on a field called *description* containing the phrase *batman*.

```json
{
    "where": [{
        "field": "description",
        "contains": "batman"
    }]
}
```



### EndsWith
This would find any item that has a field called *wordField* with a value ending with *ing*.

```json
{
    "where": [{
        "field": "wordField",
        "endsWith": "ing"
    }]
}
```



### EqualTo
This would find any item that has a field called *blends* with a value exactly matching *5*. For string fields, the comparison is case-insensitive.

```json
{
    "where": [{
        "field": "blends",
        "equalTo": 5
    }]
}
```



### Exists
In the example any document that has a field called *fieldName* and would be returned. Documents where *fieldName* has some content would also be returned.

You can use a value of *false* if you want documents that do not contain a given field or where the field is empty or null.

```json
{
    "where": [{
        "field": "fieldName",
        "exists": true
    }]
}
```



### FreeText
In the example the field *synopsis* is searched upon for any words that match *gotham* or *dark* or *knight*.

```json
{
    "where": [{
        "field": "synopsis",
        "freeText": "gotham dark knight"
    }]
}
```


### GreaterThan
In the example any item that has a field called *first* and a value that is greater than *7* would be returned.

```json
{
    "where": [{
        "field": "first",
        "greaterThan": 7
    }]
}
```



### GreaterThanOrEqualTo
In the example any item that has a field called *first* and a value that is greater than or equal to *7* would be returned.

```json
{
    "where": [{
        "field": "first",
        "greaterThanOrEqualTo": 7
    }]
}
```



### In
In the example any document where the field *first* is equal to *1*,*7* or *11* would be returned. The values should be of the same type, in this case *integer*.

```json
{
    "where": [{
        "field": "first",
        "in": [1, 7, 11]
    }]
}
```



### LessThan
In the example any item that has a field called *first* and a value that is less than *7* would be returned.

```json
{
    "where": [{
        "field": "first",
        "lessThan": 7
    }]
}
```



### LessThanOrEqualTo
In the example any item that has a field called *first* and a value that is less than or equal to *7* would be returned.

```json
{
    "where": [{
        "field": "first",
        "lessThanOrEqualTo": 7
    }]
}
```



### StartsWith
In the example if the *name* field contains a value starting with *war* it would match.

```json
{
    "where": [{
        "field": "name",
        "startsWith": "war"
    }]
}
```


### DistanceWithin
In the example any locations within a 10 mile radius of the specified location would match.

```json
{
    "where": [{
        "field": "location",
        "distanceWithin": {
            "lat": "52.377",
            "lon": "-2.749",
            "distance": "10mi"
        }
    }]
}
```
