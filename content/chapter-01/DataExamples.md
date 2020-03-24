# Data Examples

* Hello World example
  ```
  POST http://localhost:9200/index-name/_doc/document-id {
    "message": "Hello World!"
  }
  ```
* Nested document, data aggregated to remove need for joins
  ```
  POST http://localhost:9200/index-name/_doc/document-id {
    "message": "Hello World!",
    "keywords": [
        "cheerful",
        "happy"
    ]
  }
  ```



