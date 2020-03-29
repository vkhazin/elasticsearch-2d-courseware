# Performance Tuning

* Start with a configuration of the cluster and its nodes: data, master, and client nodes
* Guesstimate usage pattern: lots of searches, vs. lots of indexing, vs. lots of aggregation
* OS Configuration: number of open file descriptors shall be set to, at least, 32K-64K
* OS Configuration: disable memory swapping
* Mapping and data-modelling selection: \_all, \_source, and multi-fields mapping operations are increasing the load on the cluster
* Search vs. Filter - do you need to compute a score based on the 'status: active' in your query?
* Use [\_bulk Api](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-bulk.html) for indexing whenever possible
* Number of replicas and number of shards: availability and scaling-out vs. speed of writes dilemma



