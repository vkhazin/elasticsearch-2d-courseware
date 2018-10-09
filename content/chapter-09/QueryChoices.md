# Query Choices #

* Avoid wild-card and regex queries to increase performance
* When using full-text and non-analyzed searches on the same filed - use multi-fields
* Return fields required only, rather than all the fields:
```
curl 'localhost:9200/ordering/order/_search?pretty=true' -d '
{
    "stored_fields": ["planedOn"]
}'
```
* Use filter whenever possibly to suppress scoring:
```
curl -XPOST 'localhost:9200/ordering/order/_search?pretty=true' -d '
{
   "query": {
      "bool": {
         "filter": {
            "term": { "status": "pending" }
         }
      }
   }
}'
```