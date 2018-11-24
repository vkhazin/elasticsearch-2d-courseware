# One Node Setup Exercise #

1. Login into your sandbox
2. Update distro using terminal window:
```
sudo apt-get update && sudo apt-get install apt-transport-https -y
```
3. Install Java Runtime Environment using terminal window
```
sudo apt-get install default-jre -y
```
4. Download and install Public Signing Key:
```
curl https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
5. Add repository definition:
```
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" \
| sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
```
6. Install Elastic Search:
```
sudo apt-get update && sudo apt-get install elasticsearch
```
7. Start Elastic Search service:
```
sudo service elasticsearch start
```
8. We will be using 'curl' to troubleshoot setup and to run our first queries before we install and configure Kibana
9. Give it a moment to finish the initialization and verify it is running:
```
curl localhost:9200
```
10. Expected response:
```
{
  "name" : "lf6yb_i",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "MK-dEq3mT7W16Qw3DQRf3w",
  "version" : {
    "number" : "6.1.1",
    "build_hash" : "bd92e7f",
    "build_date" : "2017-12-17T20:23:25.338Z",
    "build_snapshot" : false,
    "lucene_version" : "7.1.0",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```
11. Posting first document:
```
curl -XPOST 'localhost:9200/orders/orders/1?pretty=true' \
    -H 'content-type: application/json' \
    -d '{
  "id": "1", 
  "placedOn": "2016-10-17T13:03:30.830Z",
  "status": "shipped"
}'
```
12. Expected Response:  
```json
  {
    "_index" : "orders",
    "_type" : "orders",
    "_id" : "1",
    "_version" : 2,
    "result" : "created",
    "_shards" : {
      "total" : 2,
      "successful" : 1,
      "failed" : 0
    },
    "_seq_no" : 0,
    "_primary_term" : 1
  }
```
13. ```_seq_no```: unique sequence of indexing operation
14. ```_primary_term```: shard id where primary copy stored
15. First query:
```
curl 'localhost:9200/orders/orders/_search?pretty=true&q=id:1'
```
16. Please review results - where are: doc id, document data, index name, type name, and search score? 
