# Creating a Docker Image & Running a Container #

* Docker images are build using Dockerfile definitions
* E.g. hello-world image:
```
FROM scratch
COPY hello /
CMD ["/hello"]
```
* Where 'scratch' is name:tag of base image, in this case most basic image 'scratch:latest'
* 'COPY' command copies executable file 'hello' to the root of file system
* 'CMD' is command executed when container is running
* Elastic Search offers number of ready-to-use <a href="https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html" target="_blank">docker images</a>
* To run Open Source Search official image:
```
 sudo docker run -d -p 9201:9200 -e "http.host=0.0.0.0" \
     -e "transport.host=127.0.0.1" \
     docker.elastic.co/elasticsearch/elasticsearch-oss:6.1.1
```
* -d: run in a detached mode
* -e: define listener ip for API and for cluster communication
* -p: map host port to container port