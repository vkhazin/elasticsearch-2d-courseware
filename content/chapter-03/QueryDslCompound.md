# Query Dsl Compound Clause

* [Combing leaf query clauses](https://www.elastic.co/guide/en/elasticsearch/reference/current/compound-queries.html)
* `bool` is frequently used:
  ```
  curl 'localhost:9200/orders/_search?pretty=true' \
  -H 'content-type:application/json' \
  -d '{
  "query" : {
    "bool" : {
      "must" : {
        "term" : { "id" : "1" }
      },
      "should": {
        "query_string" : { 
            "query" : "trackingId:*" 
        }
      }
    }
  }
  }'
  ```



