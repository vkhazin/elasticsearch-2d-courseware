# CPU Planning #

* Indexing takes CPU
* Querying takes CPU
* Aggregation takes CPU
* Badly constructed queries take more CPU
* RegEx queries burn more or less CPU, depending on how they are [constructed](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-regexp-query.html)
* Stress test and observe before you conclude on the CPU requirements