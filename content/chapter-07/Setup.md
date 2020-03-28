# Setup and Configuration #

1. Kibana is an open source product installed separately from Elastic Search
2. Can be downloaded from [Elastic.co](https://www.elastic.co/downloads/kibana) or installed using [Linux Repositories](https://www.elastic.co/guide/en/kibana/current/setup.html#setup-repositories)
3. Configuration file: /etc/kibana/kibana.yml
4. Important settings:
  ```
  server.port: 5601
  server.host: "0.0.0.0"
  elasticsearch.url: "http://localhost:9200"
  ```
5. Additional settings are detailed [here](https://github.com/elastic/kibana/blob/master/config/kibana.yml)
6. Kibana can be installed on the same nodes where Elastic Search is running, or on separate nodes
7. Kibana stores its configuration data in ElasticSearch 
8. Accessing Kibana from browser: http://ip-address:5601, where ip-address is the same as for SSH connection