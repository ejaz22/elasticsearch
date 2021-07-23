# Term Level Queries

- term level queries are not analyzed

#### Wildcard Search - Adding an asterisk for any characters (zero or more)

```json
GET /products/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veg*ble"
    }
  }
}
```

#### Wildcard Search - Adding a question mark for any single character

```json
GET /products/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veg?ble"
    }
  }
}
```

```json
GET /products/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veget?ble"
    }
  }
}
```

#### Searching with regular expressions

```json
GET /products/_search
{
  "query": {
    "regexp": {
      "tags.keyword": "Veg[a-zA-Z]+ble"
    }
  }
}
```

#### Searching for multiple terms

```json
GET /products/_search
{
  "query": {
    "terms": {
      "tags.keyword": [ "Soup", "Cake" ]
    }
  }
}
```

#### Matching documents with a value of `true` for the `is_active` field

```json
GET /products/_search
{
  "query": {
    "term": {
      "is_active": true
    }
  }
}
```

```json
GET /products/_search
{
  "query": {
    "term": {
      "is_active": {
        "value": true
      }
    }
  }
}
```

#### Retrieving documents based on IDs

```json
GET /products/_search
{
  "query": {
    "ids": {
      "values": [ 1, 2, 3 ]
    }
  }
}
```

#### Matching documents with range values

```json
GET /products/_search
{
  "query": {
    "range": {
      "in_stock": {
        "gte": 1,
        "lte": 5
      }
    }
  }
}
```

#### Matching documents with a date range

```json
GET /products/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2010/01/01",
        "lte": "2010/12/31"
      }
    }
  }
}
```

#### Matching documents with a date range and custom date format

```json
GET /products/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "01-01-2010",
        "lte": "31-12-2010",
        "format": "dd-MM-yyyy"
      }
    }
  }
}
```

##### Matching documents with non-null values

```json
GET /products/_search
{
  "query": {
    "exists": {
      "field": "tags"
    }
  }
}
```

#### Matching based on prefixes -Matching documents containing a tag beginning with `Vege`

```json
GET /products/_search
{
  "query": {
    "prefix": {
      "tags.keyword": "Vege"
    }
  }
}
```
