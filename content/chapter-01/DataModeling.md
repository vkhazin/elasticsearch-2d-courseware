# Data Modeling Best Practices

* Document is a unit of storage, indexing, search, and aggregation
* 3rd form of [normalization](https://en.wikipedia.org/wiki/Database_normalization) \(or beyond\) does not apply to ElasticSearch
* ElasticSearch supports no join or its equivalents
* Document indexing, searching, and aggregation uses no locks
* ElasticSearch designed for scalability
* Application side joins: a no-no in a Rdbms world and is a common practice in NoSql world
* Data de-normalization: redundant copies of data in each document removes the need for joins
* Nested objects: storing parent and child data in a single document
* Parent-Child Relationship: storing child documents separately and are associated with the parent document
* ElasticSearch lacks built-in mechanism for de-normalized data maintenance, so are many other NoSql



