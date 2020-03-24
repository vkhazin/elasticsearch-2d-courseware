# Mapping Exercise

1. Login into your sandbox
2. We have not yet configured elasticsearch service to start automatically, start it manually:
   ```
   sudo systemctl start elasticsearch
   ```
3. Service will start but listener will take its time before responding to incoming requests:
   ```
   curl localhost:9200
   ```
4. Give it few minutes before you get json response
5. Post new document:
   ```
   curl -XPOST localhost:9200/orders/_doc/1 \
    -H 'content-type: application/json' \
    -d '
   {
    "id": "1", 
    "placedOn": "2016-10-17T13:03:30.830Z"
   }'
   ```
6. Fetch mapping:
   ```
   curl 'localhost:9200/orders/_doc/_mapping?pretty=true'
   ```
7. Expected response:
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
8. Try modifying existing mapping:
   ```
   curl -XPUT 'localhost:9200/orders/_mapping?pretty=true' \
    -H 'content-type: application/json' \
    -d '
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
              "type" : "date",
              "format" : "strict_date_optional_time||epoch_millis"
            }
          }
        }
      }
    }
   }'
   ```
9. What's the outcome? And why?
10. Try modifying existing type mapping:
    ```
    curl -XPUT 'localhost:9200/orders/_doc/_mapping?pretty=true' \
    -H 'content-type: application/json' \
    -d '{
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
              "type" : "date",
              "format" : "strict_date_optional_time||epoch_millis"
            }
          }
        }
      }
    }
    }'
    ```
11. What now? Why?
12. Let us try again:
    ```
    curl -XPUT 'localhost:9200/orders/_doc/_mapping?pretty=true' \
    -H 'content-type: application/json' \
    -d '
    {
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
          "type" : "date",
          "format" : "strict_date_optional_time||epoch_millis"
        }
      }
    }
    }'
    ```
13. Did it work? What's the difference?
14. Let's modify data type for existing field
    ```
    curl -XPUT 'localhost:9200/orders/_doc/_mapping?pretty=true' \
    -H 'content-type: application/json' \
    -d '
    {
    "_doc" : {
      "properties" : {
        "id" : {
          "type" : "double"
        },
        "placedOn" : {
          "type" : "date",
          "format" : "strict_date_optional_time||epoch_millis"
        }
      }
    }
    }'
    ```
15. Seriously, what now? Why? So much for the dynamic data mapping?
16. What if we need to change data type after we have indexed the data?
17. There is no \(more\) option to delete the mapping - delete and recreate index is the only option :-\(

    ```
    curl -XDELETE localhost:9200/orders

    curl -XPUT 'localhost:9200/orders?pretty=true' \
    -H 'content-type: application/json' \
    -d '
    {
    "settings" : {
      "number_of_shards" : 3,
      "number_of_replicas" : 2
    },
    "mappings" : {
      "_doc" : {
        "properties" : {
          "id" : {
            "type" : "double"
          },
          "placedOn" : {
            "type" : "date",
            "format" : "strict_date_optional_time||epoch_millis"
          }
        }
      }
    }
    }'
    ```

18. Use json data from the previous step to define the mapping
19. Watch out: there is no warning or confirmation using curl!
20. Psst: look out for the proper response too:
    ```
    {
    "acknowledged" : true,
    "shards_acknowledged" : true,
    "index" : "orders"
    }
    ```



