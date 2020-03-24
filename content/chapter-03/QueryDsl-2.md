# Query Dsl Cont'd

* Leaf query clause: an equivalent of where clause in a sql statement for a particular field value
* `query_string` Json property to use Lucene syntax e.g.: `id:1`
* Compound query clause: an equivalent of `and`, `or`, `not`, and etc. operators in sql statement
* `bool` represents boolean combinations of other queries, e.g.: `must` and `filter`
* `must` represents a condition that must be matched and will be used for computing score or relevancy of the search result
* `filter` acts similarily to search but does not contribute to the computation of score or relevancy of a document
* Additional options for bool are: ['should' and 'must\_not'](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-bool-query.html)



