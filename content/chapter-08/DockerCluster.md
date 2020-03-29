# Docker Cluster

* In our exercise, we have used single docker host
* For production, we rather use multiple hosts to run our containers
* [Docker Swarm](https://docs.docker.com/engine/swarm/) provides orchestration up-to 1,000 nodes and 30,000 containers
  ![Swarm Diagram](../../media/swarm-diagram.png)
* docker-compose orchestrates launching multiple containers at once using [docker-compose.yml](https://github.com/darienmt/airplane-adventures/blob/master/Docker/elk-containers/docker-compose.yml)
* In addition to Docker Swarm there is also [Google Kubernetes](https://kubernetes.io/), [Apache Mesos](http://mesos.apache.org/), and likely others
* [Comparison from techgenix](http://techgenix.com/swarm-kubernetes-mesos/)
* Kubernetes seems to be a market favourite at the moment
* In addition to the self-hosted version of docker, there are Aws Kubernetes Service, Google Container Engine, Docker Cloud, and Azure Container Service



