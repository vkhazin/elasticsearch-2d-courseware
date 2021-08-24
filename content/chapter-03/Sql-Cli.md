# Sql-Cli

* There is also [sql-cli](https://www.elastic.co/guide/en/elasticsearch/reference/current/sql-cli.html):
  ```
  sudo /usr/share/elasticsearch/bin/elasticsearch-sql-cli localhost:9200
  ```
* From inside the shell, you can run sql statements directly e.g.:
  ```
  select ACC_DATE, BARRACK, CASE_NUMBER from collisions where BARRACK='Rockville' limit 5;
  ```
* Result:
  ```
         ACC_DATE       |    BARRACK    |  CASE_NUMBER  
  ----------------------+---------------+---------------
  01/01/2012 12:00:00 AM|Rockville      |1363000002     
  01/01/2012 12:00:00 AM|Rockville      |1263000017     
  01/02/2012 12:00:00 AM|Rockville      |1263000025     
  01/03/2012 12:00:00 AM|Rockville      |1263000068     
  01/03/2012 12:00:00 AM|Rockville      |1263000054
  ```
* There is also a schema querying syntax:
  ```
  describe collisions;
  ```
* Result:
  ```
            column           |     type      |    mapping    
  ---------------------------+---------------+---------------
  ACC_DATE                   |VARCHAR        |text           
  ACC_DATE.keyword           |VARCHAR        |keyword        
  ACC_TIME                   |VARCHAR        |text           
  ACC_TIME.keyword           |VARCHAR        |keyword        
  ACC_TIME_CODE              |VARCHAR        |text           
  ...
  ```



