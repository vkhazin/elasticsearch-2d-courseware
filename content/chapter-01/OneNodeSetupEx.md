# One Node Setup Exercise

1. Login into your sandbox using SSH
2. Update package list:
   ```
   sudo apt-get update
   ```
3. Install Java Runtime Environment:
   ```
   sudo apt-get install default-jre -y
   ```
4. Download and install Public Signing Key:
   ```
   curl https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
   ```
5. Add repository definition:
   ```
   echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" \
    | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
   ```
6. Install Elastic Search:
   ```
   sudo apt-get update && sudo apt-get install elasticsearch
   ```
7. Start Elastic Search service:
   ```
   sudo systemctl start elasticsearch
   ```
8. We will be using 'curl' to troubleshoot the setup and to run our first queries before we install and configure Kibana
9. Give it a moment to finish the initialization and verify it is running:
   ```
   curl localhost:9200
   ```
10. Expected response:
    ```
    {
      "name" : "ip-172-31-19-36",
      "cluster_name" : "elasticsearch",
      "cluster_uuid" : "9NP9kO4-S8qm8tMExZg9YA",
      "version" : {
        "number" : "7.6.1",
        "build_flavor" : "default",
        "build_type" : "deb",
        "build_hash" : "aa751e09be0a5072e8570670309b1f12348f023b",
        "build_date" : "2020-02-29T00:15:25.529771Z",
        "build_snapshot" : false,
        "lucene_version" : "8.4.0",
        "minimum_wire_compatibility_version" : "6.8.0",
        "minimum_index_compatibility_version" : "6.0.0-beta1"
      },
      "tagline" : "You Know, for Search"
    }
    ```
11. Posting the first document:
    ```bash
    curl -XPOST 'localhost:9200/orders/_doc/1?pretty=true' \
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
      "_type" : "_doc",
      "_id" : "1",
      "_version" : 1,
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
13. `_seq_no`: unique sequence of the indexing operation
14. `_primary_term`: shard id where primary copy stored
15. First query:
    ```
    curl 'localhost:9200/orders/_doc/_search?pretty=true&q=id:1'
    ```
16. Where are: doc id, document data, index name, type name, and search score?
17. Next time you can run the setup script at once:
    ```
    curl https://gist.githubusercontent.com/vkhazin/6b0e44387368439af8e1750a1a0fa008/raw/02bbac1f7bf0c76e3dd49284da28f253f8ad5c73/Install%2520ElasticSearch%2520v7%2520on%2520Ubuntu%252018.04 \\
     | bash -
    ```



