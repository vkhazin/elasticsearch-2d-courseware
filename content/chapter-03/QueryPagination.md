# Query Pagination

* Query results are limited to a page size of 10 by default
* Query pagination and page number controlled by From/Size parameters:
  ```
  curl -XPOST 'localhost:9200/orders/_search?pretty=true' \
  -H 'content-type: application/json' \
  -d '
  { 
    "from":0, 
    "size":2, 
    "query": {
      "match_all":{}
    }
  }'
  ```
* Expected result \(partially presented\):
  ```
  {
  ...
  "hits" : {
    "total" : {
      "value" : 1,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "orders",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "id" : "1",
          "placedOn" : "2016-10-17T13:03:30.830Z"
        }
      },
      ...
    ]
  }
  }
  ```
* Note `hits.total.value` field, what does it stand for?
* How results are sorted?



