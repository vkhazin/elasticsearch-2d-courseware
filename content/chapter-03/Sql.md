# Sql

* Access full-text search, blazing speed, and effortless scalability using a familiar query syntax
* Example: 
  ```
  curl -POST 'localhost:9200/_xpack/sql?format=txt' \
      -H 'content-type:application/json' \
      -d '{ "query": "SELECT ACC_DATE, ACC_TIME, BARRACK FROM collisions LIMIT 5"}'

  ```
* Result:
  ```
         ACC_DATE       |   ACC_TIME    |    BARRACK     
  ----------------------+---------------+----------------
  01/01/2012 12:00:00 AM|2:01           |Rockville       
  01/01/2012 12:00:00 AM|18:01          |Berlin          
  01/01/2012 12:00:00 AM|7:01           |Prince Frederick
  01/01/2012 12:00:00 AM|0:01           |Leonardtown     
  01/01/2012 12:00:00 AM|1:01           |Essex
  ```



