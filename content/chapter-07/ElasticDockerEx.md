# Docker Setup Exercise #

* Login into your sandbox
* Since previously installed Elastic is running, we will use a different port: 9201 for api
* Give it few moments to start and then test:
```
 curl elastic:changeme@localhost:9201
```
* Expected output:
```
{
  "name" : "3kMnHFQ",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "E7Ag9a_1SX2FVPsMQGUCng",
  "version" : {
    "number" : "5.4.1",
    "build_hash" : "2cfe0df",
    "build_date" : "2017-05-29T16:05:51.443Z",
    "build_snapshot" : false,
    "lucene_version" : "6.5.1"
  },
  "tagline" : "You Know, for Search"
}
```
* Using docker cli to list containers:
```
sudo docker ps -a
```
* Expected output:
```
CONTAINER ID        IMAGE                                                 COMMAND                  CREATED             STATUS                      PORTS                              NAMES
8ed07e81b59c        docker.elastic.co/elasticsearch/elasticsearch:5.4.1   "/bin/bash bin/es-doc"   12 minutes ago      Up 12 minutes               9300/tcp, 0.0.0.0:9201->9200/tcp   modest_almeida
d17b7a47d139        hello-world                                           "/hello"                 57 minutes ago      Exited (0) 57 minutes ago                                      distracted_darwin
```
* To stop running container, copy CONTAINER_ID to replace in the command below:
```
sudo docker stop 8ed07e81b59c

```
* Using docker cli to list containers to confirm none are running:
```
sudo docker ps -a
```
* Expected output:
```
CONTAINER ID        IMAGE                                                 COMMAND                  CREATED             STATUS                        PORTS               NAMES
8ed07e81b59c        docker.elastic.co/elasticsearch/elasticsearch:5.4.1   "/bin/bash bin/es-doc"   14 minutes ago      Exited (143) 10 seconds ago                       modest_almeida
d17b7a47d139        hello-world                                           "/hello"                 59 minutes ago      Exited (0) 59 minutes ago                         distracted_darwin

```
