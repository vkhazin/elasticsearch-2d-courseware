# Creating a Docker Image & Running a Container

* Docker images are build using Dockerfile definitions
* E.g. hello-world image:
  ```
  FROM scratch:latest
  COPY hello /
  CMD ["/hello"]
  ```
* Where 'scratch' is name of a base image, in this case most basic image 'scratch:latest'
* 'COPY' command copies executable file 'hello' to the root of file system
* 'CMD' is a command executed when the container is running
* Elastic Search offers number of ready-to-use [docker images](https://www.docker.elastic.co/)
* To run elastic search open-source official image:
  ```
  sudo docker run -d -p 9201:9200 -e "http.host=0.0.0.0" \
     -e "transport.host=127.0.0.1" \
     docker.elastic.co/elasticsearch/elasticsearch-oss:7.6.1
  ```
* -d: run in a detached mode
* -e: define listener ip for API and for cluster communication
* -p: map host port to container port



