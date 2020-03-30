# Query Exercise

* Login into your ElasticSearch sandbox
* Make sure elastic search is running:
  ```
  sudo systemctl restart elasticsearch
  ```
* Populate a few orders:

  ```
  curl -XPOST localhost:9200/orders/_doc/2 \
  -H 'content-type: application/json' \
  -d '
  {
  "id": "2", 
  "placedOn": "2017-01-01T00:00:00Z", 
  "status": "pending"
  }'
  ```

  ```
  curl -XPOST localhost:9200/orders/_doc/3 \
  -H 'content-type: application/json' \
  -d '
  {
  "id": "3", 
  "placedOn": 
  "2016-10-01T00:00:00Z", 
  "status": "shipped"
  }'
  ```

  ```
  curl -XPOST localhost:9200/orders/_doc/4 \
  -H 'content-type: application/json' \
  -d '
  {
  "id": "4", 
  "placedOn": "2016-01-01T00:00:00Z", 
  "status": "received"
  }'
  ```

* Confirm there are some records to search on:
  ```
  curl 'localhost:9200/orders/_search?pretty=true'
  ```
* How many documents did you find?
* How do you know whether you received all the documents or just the first page of records?
* How do you find all the orders that were shipped?
* What is the order of the results?
* How do you [sort](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-request-sort.html) results using an arbitrary field?
* Pick a couple of options and run your sort query
* Reformat your query to use query Uri instead of query Json
* You will be asked to present your sort findings to others...



