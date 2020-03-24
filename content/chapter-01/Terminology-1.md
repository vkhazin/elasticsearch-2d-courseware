# Terminology

* ElasticSearch is a near real-time search platform built on top of [Apache Lucene](https://lucene.apache.org/core/)
* ElasticSearch supports [ACID](https://en.wikipedia.org/wiki/ACID) for a single document only
* Cluster is a collection of one or more nodes storing, indexing, and searching data
* Node is a single server in a cluster, nodes discover each other with unicast and by cluster name defined in /etc/elasticsearch/elasticsearch.yml
* Node can be configured as master-eligible, data, client, tribe, or left default: master-eligible and data node
* Index is a collection of documents and equivalent of Rdbms \(Relational Database Management System\) database or schema
* Type is a collection of documents of a specific type inside the index, a loose equivalent of a table in Rdbms
* Document is a basic unit of operation for indexing, replications, and searching. An approximate equivalent of a row/record in Rdbms.
* Document is stored in an index's shard



