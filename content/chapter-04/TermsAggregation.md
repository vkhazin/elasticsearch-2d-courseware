# Terms Aggregation #

* Terms aggregation query: 
```
curl -XPOST 'http://localhost:9200/orders/orders/_search?pretty=true' \
  -H 'content-type: application/json' \
  -d '
{
  "size": 0, 
  "aggregations": {
    "order-status": {
      "terms": {
        "field": "status.keyword"
      }
    }
  }
}'
```
* "size": 0 - suppress query results to fetch aggregations results only
* "aggregations" or "aggs" - part of ElasticSearch Dsl
* "order-status" - an arbitrary name for aggregation
* "terms" - type of aggregation to use
* Results:
```
{
  "took" : 44,
  "timed_out" : false,
  "_shards" : {
    "total" : 5,
    "successful" : 5,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : 4,
    "max_score" : 0.0,
    "hits" : [ ]
  },
  "aggregations" : {
    "order-status" : {
      "doc_count_error_upper_bound" : 0,
      "sum_other_doc_count" : 0,
      "buckets" : [
        {
          "key" : "pending",
          "doc_count" : 1
        },
        {
          "key" : "received",
          "doc_count" : 1
        },
        {
          "key" : "shipped",
          "doc_count" : 1
        }
      ]
    }
  }
}
```