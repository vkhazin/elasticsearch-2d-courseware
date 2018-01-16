# Setup and Configuration #

1. Kibana is an open source product installed separately from Elastic Search
2. Can be downloaded from <a href="https://www.elastic.co/downloads/kibana" target="_blank">Elastic.co</a> or installed using <a href="https://www.elastic.co/guide/en/kibana/current/setup.html#setup-repositories" target="_blank">Linux Repositories</a>
3. Configuration file: /etc/kibana/kibana.yml
4. Important settings:
  ```
  server.port: 5601
  server.host: "0.0.0.0"
  elasticsearch.url: "http://localhost:9200"
  ```
5. Additional settings are detailed <a href="https://github.com/elastic/kibana/blob/master/config/kibana.yml" target="_blank">here</a>
6. Kibana can be installed on the same nodes where Elastic Search is running, or on separate nodes
7. Kibana stores its configuration data in ElasticSearch 
8. Accessing Kibana from browser: http://ip-address:5601, where ip-address is the same as for SSH connection