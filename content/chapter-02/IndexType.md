# Index

* An index is broken down, stored, and processed as a collection of shards
* Shards are allocated to nodes and are searched independently
* A type used to be a mechanism to store different data in the same index and has been deprecated
* Searching within index, between index and between shards adds no overhead, almost
* A score for search results calculated at the index level
* Mapping for document's properties are defined at the type level
* Search and aggregation can be executed at type, index, alias, multi-index, or at cluster levels
* With v6 Elastic has dropped support for multiple types in the same index



