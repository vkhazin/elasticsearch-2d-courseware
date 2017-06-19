# Filter #

* Leaf and Compound components of the search Dsl can be used in query and in filter context
* So far we have been using Search Dsl in the query context
* Filtering context is a 'non-scoring' or 'filtering' query - yes/no answer, no score is computed
* Typical use of query is to find a best matching document, similar to Google Search
* Scoring calculates how relevant each document is, relative to the search criteria
* Filtering is used to exclude documents from search result without computing a score