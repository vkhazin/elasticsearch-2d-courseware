# Capacity Planning #

* How many nodes?
* The basic starting point is two nodes with 2 cores and 4GB of memory on each node
* For fault tolerance perspective three nodes is more appropriate for any [cluster](http://stackoverflow.com/questions/2330562/do-i-absolutely-need-a-minimum-of-3-nodes-servers-for-a-cassandra-cluster-or-wil)
* What's better more nodes or bigger nodes?
* More nodes equals IO, Memory, and GC (garbage collector) distributed processing
* Bigger nodes means more processing can be performed on a node with fast access to in-memory data and faster local IO
* Resizing node in production is likely more challenging than adding a new node to the cluster
* [ElasticSearch is built for scaling out on commodity hardware, not up on a single massive machine](https://www.elastic.co/blog/found-elasticsearch-in-production)
* How high can ElasticSearch go? [Pretty high](https://grey-boundary.io/field-notes-elasticsearch-at-petabyte-scale-on-aws/)
