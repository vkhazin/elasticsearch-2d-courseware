# Filebeat Setup Exercise

1. Login into your sandboxes
2. Verify ElasticSearch is running: `sudo systemctl restart elasticsearch`
3. Download public key for the repository, **not required** as we have done it before:
   ```
   curl https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
   ```
4. Add repository to the list, **not required** as we have done it before:
   ```
   echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | \
       sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list && \
       sudo apt-get update
   ```
5. Install Filebeat from the repository:
   ```
   sudo apt-get install filebeat
   ```
6. Configure the location of log files:
   ```
   sudo nano /etc/filebeat/filebeat.yml
   ```
7. Important settings:

   ```
   - type: log

    # Change to true to enable this input configuration.
    enabled: true

    # Paths that should be crawled and fetched. Glob based paths.
    paths:
      - /var/log/*.log 

   output.elasticsearch:
    hosts: ["localhost:9200"]
   ```

8. Start Filebeat service and check the status:

   ```
   sudo systemctl restart filebeat
   ```

9. Query ElasticSearch using `curl` to confirm new index has been created e.g.: `filebeat-7.6.1-2020.03.28-000001`

   ```
   curl localhost:9200/_cat/indices
   ```

10. Query the data inside the newly created index
11. Review more [options](https://www.elastic.co/guide/en/beats/filebeat/current/elasticsearch-output.html) for elastic search output



