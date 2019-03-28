# Sql

* Access full text search, blazing speed, and effortless scalability using a familiar query syntax
* Example: 
```
curl -POST 'localhost:9200/_xpack/sql?format=txt' \
  -H 'content-type:application/json' \
  -d '
  {
      "query": "SELECT * FROM orders"
  }'
```
* Result:
```
      id       |        placedOn        |    status     
---------------+------------------------+---------------
1              |2016-10-17T13:03:30.830Z|shipped
...
```
