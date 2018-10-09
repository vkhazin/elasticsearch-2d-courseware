# Memory Planning #

* If I plan to store X documents with Y KB in size - what's the formula for memory requirements?
* Search engines including ElasticSearch perform the best when the data and indices are cached in memory
* What's the usage patters will be:
  * How many aggregate queries vs. filtered queries vs. scan queries would you run?
  * How many request per second of each type are you planning to support?
  * How often will you be taking full snapshots and incremental snapshots?
* How much memory is enough memory?
* OutOfMemory-errors can result in many things going awry, ElasticSearch is not a database per ce, hence ['does not look before it leaps'](https://www.elastic.co/blog/found-elasticsearch-in-production#outofmemory-caused-crashes)
* Approach recommended publically by Elastic: "start out with more memory than you need and scale down to find the sweet spot"
* Approach recommended privately by Elastic: find our how much a single node can handle and then extrapolate the number of nodes
* Do not enable memory disk swap! <a href="https://www.elastic.co/guide/en/elasticsearch/guide/current/heap-sizing.html#_swapping_is_the_death_of_performance" target="_blank">deadly</a>
* Swap file might also need to be disabled for other NoSql as well e.g.:<a href="http://stackoverflow.com/questions/22988824/why-swap-needs-to-be-turned-off-in-datastax-cassandra" target="_blank">Cassandra</a>
