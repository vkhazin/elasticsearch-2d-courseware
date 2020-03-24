# Cluster, Shards, and Replicas

* How many nodes in the cluster?
* A shard cannot be split between nodes, a shard is a complete Lucene index
* The question, therefore, is how many shards per cluster and then per node
* Max Jvm Heap size recommended for ElasticSearch: 32GB
* Jvm Heap size recommended at half of the RAM
* Number of shards is often based on the dataset size and many organizations mistakenly over-allocate
* How many replicas should I have?
* You may have guessed the answer - it depends...
* Number of replicas affects more than fault tolerance: write performance, read performance, and [split-brain](https://github.com/elastic/elasticsearch/issues/2488) problem
* Fault tolerance rule is N+1, therefore is you would like your data to be stored twice - replica settings should be equal to 2
* Write performance - in extreme cases index request to cluster will time-out when the number of available nodes is less than the number of replicas configured for the index
* Read performance - search uses replicas as well, more replicas should result in faster searches and aggregations
* Split-brain problem - no permanent solution, designated nodes complicate cluster setup and operation, but offer more granular control.



