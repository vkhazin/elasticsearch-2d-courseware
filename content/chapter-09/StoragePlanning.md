# Storage Planning #

* Raw document size
* `_all` is a special field to search on all fields
* doc_values mentioned in parent-child relationship, reduce heap size 
* analyzed vs. not_analyzed mapping
* [LZ4 compression settings](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules.html#_static_index_settings)
* Data to storage requirements [article](https://www.elastic.co/blog/elasticsearch-storage-the-true-story) lists ranges from 0.6 to 1.4 depending on the compression and other options
* In addition to ElasticSearch data take in consideration snapshots, logs, and operating system data.
* Maybe safe bet is to 1.5 of the anticipated data volume, but that also means over-allocating
