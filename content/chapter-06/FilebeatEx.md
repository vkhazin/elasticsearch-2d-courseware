# Filebeat Setup Exercise #

1. Login into your sandboxes
2. Verify ElasticSearch is running: ```sudo service elasticsearch restart```
3. Download public key for the repository:
  ```
  curl https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
  ```
4. Add repository to the list:
  ```
  echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
  ```
5. Install Filebeat from the repository:
  ```
  sudo apt-get update && sudo apt-get install filebeat
  ```
6. Configure the logs location:
  ```
  sudo nano /etc/filebeat/filebeat.yml
  ```
7. Important settings:  
  ```
  - type: log

    # Change to true to enable this prospector configuration.
    enabled: true

    # Paths that should be crawled and fetched. Glob based paths.
    paths:
      - /var/log/*.log 

  output.elasticsearch:
    hosts: ["localhost:9200"]
  ```
8. Start Filebeat service and check the status:  
  ```
  sudo service filebeat start && sudo service filebeat status
  ```
9. Query ElasticSearch using `curl` to confirm new index has been created e.g.: filebeat-6.1.1-2018.01.13
  ```
  curl localhost:9200/_cat/indices
  ```
10. Query the data inside the newly created index
11. Review more [options](https://www.elastic.co/guide/en/beats/filebeat/current/elasticsearch-output.html) for elasticsearch output
