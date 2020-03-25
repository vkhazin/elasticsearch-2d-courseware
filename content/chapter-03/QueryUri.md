# Query Uri

* In addition to Json Dsl there is [URI Search](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-uri-request.html)
* Support is more limited than Json Dsl, but Kibana seems to be just fine with it
* **q** parameter allows specifying query in Lucene formatted query:
  ```
  curl 'localhost:9200/orders/_search?q=placedOn:*&pretty=true'
  ```
* Expected result:
  ```
  {
  ...
  "hits" : {
    "total" : 1,
    "max_score" : 0.30685282,
    "hits" : [ 
      {
        "_index" : "ordering",
        "_id" : "3",
        "_score" : 0.30685282,
        "_source" : {
          "id" : "3",
          "placedOn" : "2016-10-01T00:00:00Z",
          "status" : "shipped"
        }
      }, 
      ...
    ]
  }
  }
  ```



