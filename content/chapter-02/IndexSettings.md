# Index Settings

* An Index can be created explicitly using index API
* Number of shards are defined when an index is created
* Number of shards cannot be changed after the index has been created
* The number of replicas can be updated on an existing index:
  ```
  PUT /index-name/_settings
  {
    "number_of_replicas": 5
  }
  ```
* The number of replicas can be configured dynamically:
  ```
  index.auto_expand_replicas: 0-5
  ```
* Query size can be limited to conserve heap memory:
  ```
  index.max_result_window: 10000
  ```
* [More index settings](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules.html)



