# Terminology - Cont'd #

* Shard is a unit of storage and operation assigned to a node to distribute index across nodes in a cluster - to allow horizontal scalability
* Replication supports high availability as in case of a node failure and improves scalability by allowing search operations on replicas
* Clustering across multiple data centers, i.e. higher network latency and lower bandwidth is not supported
* New in ElasticSearch 6.7 is [CCR](https://www.elastic.co/blog/elasticsearch-6-7-0-released): cross-cluster-replication

<img src="../../media/multi-DC.png" style="align:center" width="500pxl"/>