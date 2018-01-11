# Index and Type #

* Index is broken down, stored, and processed as collection of shards
* Shards are allocated to nodes and are searched independently
* Type is a mechanism to store different data in the same index
* Searching across types within index and between shards adds no overhead, almost
* Fields across types in an index must use consistent data types
* Score for search results calculated at the index level
* Mapping for document's properties are defined at the type level
* Search and aggregation can be executed at type, index, alias, multi-index, or at cluster levels
* With v6 Elastic has dropped support for multiple types in the same index