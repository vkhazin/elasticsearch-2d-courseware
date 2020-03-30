# Terms Aggregation

* Terms aggregation query: 
  ```
  curl -XPOST 'http://localhost:9200/collisions/_search?pretty=true' \
      -H 'content-type: application/json' \
      -d '
      {
          "size": 0,
              "aggregations": {
                  "city": {
                      "terms": {
                      "field": "CITY_NAME.keyword"
                  }
              }
          }
      }'
  ```
* "size": 0 - suppress query results to fetch aggregations results only
* "aggregations" or "aggs" - part of ElasticSearch Dsl
* "order-status" - an arbitrary name for aggregation
* "terms" - the type of aggregation to use
* Results:
  ```
  {
    ...
    "aggregations" : {
      "city" : {
        "doc_count_error_upper_bound" : 0,
        "sum_other_doc_count" : 132,
        "buckets" : [
          {
            "key" : "Not Applicable",
            "doc_count" : 18105
          },
          {
            "key" : "",
            "doc_count" : 195
          },
          {
            "key" : "Mount Airy",
            "doc_count" : 59
          },
          {
            "key" : "Berlin",
            "doc_count" : 19
          },
          {
            "key" : "Westminster",
            "doc_count" : 19
          },
          {
            "key" : "Leonardtown",
            "doc_count" : 10
          },
          {
            "key" : "Walkersville",
            "doc_count" : 9
          },
          {
            "key" : "Grantsville",
            "doc_count" : 8
          },
          {
            "key" : "Salisbury",
            "doc_count" : 8
          },
          {
            "key" : "Frederick",
            "doc_count" : 7
          }
        ]
      }
    }
  }
  ```



