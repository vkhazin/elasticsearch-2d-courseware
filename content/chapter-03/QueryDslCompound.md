# Query Dsl Compound Clause #

* <a href="https://www.elastic.co/guide/en/elasticsearch/reference/current/compound-queries.html" target="_blank">Combing leaf query clauses</a>
* ```bool``` is frequently used to emulate ```and``` clause:
```
curl 'localhost:9200/ordering/orders/_search?pretty=true' -d '{
   "query" : {
      "bool" : {
         "must" : {
            "term" : { 
                "id" : "1" 
            }
         },
         "must": {
            "query_string" : { 
               "query" : "trackingId:*" 
            }
         }
      }
   }
}'
```
