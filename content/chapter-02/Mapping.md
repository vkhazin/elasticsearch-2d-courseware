# Mapping

* Flexible schema: index a document and field mappings will be derived automatically
* Mapping defines how a document and its fields are stored and indexed
* Mapping can be derived dynamically by ElasticSearch
* A handful of core data types are [supported](https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html)
* Mapping can be added to an existing index for _**new fields**_
* Existing field mapping not always possible to modify
* ElasticSearch will derive mapping for a new type and for new fields:
  ```
  curl -XPOST localhost:9200/orders/_doc/1 \
    -H 'Content-Type: application/json' \
    -d '{"id": "1", "placedOn": "2016-10-17T13:03:30.830Z"}'
  ```
* Retrieving existing mappings: `curl 'localhost:9200/orders/_mapping?pretty=true'`
* Expected response:
  ```
  {
    "orders" : {
      "mappings" : {
        "_doc" : {
          "properties" : {
            "id" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "placedOn" : {
              "type" : "date"
            }
          }
        }
      }
    }
  }
  ```
* Rich support for [date-time formats](https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-date-format.html#built-in-date-formats)



