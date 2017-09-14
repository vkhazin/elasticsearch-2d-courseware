# Query Dsl Cont'd #

* Leaf query clause: an equivalent of where clause in a sql statement for a particular field value
* ```query_string``` json property to use Lucene syntax: ```id:1```
* Compound query clause: an equivalent of ```and```, ```or```, ```not```, and etc. operators in sql statement
* ```bool``` represents boolean combinations of other queries, e.g.: ```must``` and ```filter```
* ```must``` represents condition that must be matched and will be used for computing score or relevancy of the search result
* filter acts similirary to search but does not contribute to computation of score or relevancy of document found, more detais a bit later...
* Additional options for bool are: <a href="https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-bool-query.html" target="_blank">'should' and 'must_not'</a>