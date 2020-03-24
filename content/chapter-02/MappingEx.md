# Mapping Exercise

1. Login in to your sandbox
2. We have not yet configured elasticsearch service to start automatically, start it manually:
   ```
   sudo systemctl start elasticsearch
   ```
3. Service will start but the listener will take its time before responding to incoming requests, verify with the command:
   ```
   curl localhost:9200
   ```
4. Give it a few minutes before you get json response with a tagline `"You Know, for Search"`
5. Post a new document:
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
   curl 'localhost:9200/orders/_mapping?pretty=true'
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
10. Let us try again:
11. ```
    curl -XPUT 'localhost:9200/orders/_mapping?pretty=true' \
    -H 'content-type: application/json' \
    -d '
    {
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
    }'
    ```
12. Did it work? What's the difference?
13. Let's modify data type for existing field
    ```
    curl -XPUT 'localhost:9200/orders/_mapping?pretty=true' \
      -H 'content-type: application/json' \
      -d '{
      "properties": {
        "id": {
          "type": "double"
        },
        "placedOn": {
          "type": "date",
          "format": "strict_date_optional_time||epoch_millis"
        }
      }
    }'
    ```
14. Seriously, what now? Why? So much for the dynamic data mapping?
15. What if we need to change data type after we have indexed the data?
16. There is no \(more\) option to delete the mapping - delete and recreate index is the only option :-\(

    ```
    curl -XDELETE localhost:9200/orders

    curl -XPUT 'localhost:9200/orders?pretty=true' \
    -H 'content-type: application/json' \
    -d '
        {
            "settings": {
                "number_of_shards": 3,
                "number_of_replicas": 2
            },
            "mappings": {
                "properties": {
                "id": {
                    "type": "double"
                },
                "placedOn": {
                    "type": "date",
                    "format": "strict_date_optional_time||epoch_millis"
                }
            }
        }
    }'
    ```

17. Watch out: there is no warning or confirmation using curl!
18. Psst: lookout for the proper response too:
    ```
    {
      "acknowledged" : true,
      "shards_acknowledged" : true,
      "index" : "orders"
    }
    ```



