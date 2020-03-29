# ElasticSearch Container Exercise

1. Login into your sandbox
2. Shutdown host services to release memory:   
   ```
   sudo systemctl stop elasticsearch kibana filebeat logstash
   ```
3. Since previously installed Elastic is configured to use port 9200, we will use a different port: 9201 for the container listener
   ```
   sudo docker run -d -p 9201:9200 -e "http.host=0.0.0.0" \
     -e "transport.host=127.0.0.1" \
     docker.elastic.co/elasticsearch/elasticsearch-oss:7.6.1
   ```
4. -d: run detached not to take over command prompt
5. -e: parameters accepted/expected by the image
6. Give it a few moments to start and then test: `curl localhost:9201`
7. Expected output:
   ```
   {
    "name" : "ub7KTFp",
    "cluster_name" : "docker-cluster",
    "cluster_uuid" : "qRZeIskgTSOjrgpgAHSNAg",
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
8. Using docker cli to list containers:
   ```
   sudo docker ps -a
   ```
9. The expected output is a list with two containers: `hello-world` and `elastic`
10. To stop running container, copy `container id` to replace in the command: 
    ```
    sudo docker stop 8ed07e81b59c
    ```
11. Using docker cli to list containers to confirm none are running: `sudo docker ps -a`
12. The expected output is a list of two containers previously launched: hello-world and elasticsearch



