# Sql-Cli

* There is also [sql-cli](https://www.elastic.co/guide/en/elasticsearch/reference/current/sql-cli.html):
  ```
  $ sudo /usr/share/elasticsearch/bin/elasticsearch-sql-cli \
    localhost:9200
  ```
* From inside the shell you can run sql directly e.g.:
  ```
  select * from orders where status = 'shipped';
  ```
* Result:
  ```
      id       |        placedOn        |    status     
  ---------------+------------------------+---------------
  1              |2016-10-17T13:03:30.830Z|shipped
  ```
* There is also a schema querying syntax:
  ```
  describe orders;
  ```
* Result:
  ```
    column     |     type      |    mapping    
  ---------------+---------------+---------------
  id             |VARCHAR        |text           
  id.keyword     |VARCHAR        |keyword        
  placedOn       |TIMESTAMP      |datetime       
  status         |VARCHAR        |text           
  status.keyword |VARCHAR        |keyword
  ```



