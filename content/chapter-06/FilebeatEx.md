# Filebeat Setup Exercise #

* Login into your sandboxes
* Verify ElasticSearch is running: ```sudo service elasticsearch restart```
* Download public key for the repository:
```
curl -O - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
* Add repository to the list:
```
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
```
* Install Filebeat from the repository:
```
sudo apt-get update && sudo apt-get install filebeat
```
* Configure the logs location:
```
sudo nano /etc/filebeat/filebeat.yml
```
* Important settings:  
```
- type: log

  # Change to true to enable this prospector configuration.
  enabled: true

  # Paths that should be crawled and fetched. Glob based paths.
  paths:
    - /var/log/*.log 
    
output.elasticsearch:
  # Array of hosts to connect to.
  hosts: ["localhost:9200"]
```
* Start Filebeat service and check the status:  
```
sudo service filebeat start && sudo service filebeat status
```
* Query ElasticSearch using culr to confirm new index has been created: 'filebeat-':  
```
curl localhost:9200/_cat/indices
```
* Query the data inside the newly created index
* Review more <a href="https://www.elastic.co/guide/en/beats/filebeat/current/elasticsearch-output.html" target="_blank">options for elasticsearch output</a>
