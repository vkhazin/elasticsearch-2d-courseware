# Filter Exercise

* Login in to your ElasticSearch sandbox
* Make sure the elastic search service is running:
  ```
  sudo systemctl restart elasticsearch
  ```
* Populate few sample data borrowed from [data.gov](https://catalog.data.gov/dataset):
  ```
  curl -O https://s3.us-east-2.amazonaws.com/elasticsearch-courseware/sample-data/collisions.txt
  curl -XPOST 'localhost:9200/_bulk' -H 'content-type:application/json' --data-binary "@collisions.txt"
  ```
* Confirm there are some records to search on:
  ```
  curl 'localhost:9200/collisions/_search?pretty=true'
  ```
* How many documents did you find?
* Pick a couple of options to search on: different leaf and compound clauses, different field types
* Rewrite your queries into filtered query
* You will be asked to present your findings to others



