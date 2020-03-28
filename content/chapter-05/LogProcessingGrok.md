# Logs Processing - Grok Filter

* `grok` filter plugin is to parse the unstructured log data into something query-able
* Log data:
  ```
  2017-06-21 22:18:25,276 - util.py[DEBUG]: Reading from /proc/uptime (quiet=False)
  ```
* [Predefined match patterns](https://github.com/elastic/logstash/blob/v1.4.0/patterns/grok-patterns)
* [Custom parse patterns](https://www.elastic.co/guide/en/logstash/current/plugins-filters-grok.html#_custom_patterns) added by the author:
  ```
  For module: (?<= - )(.+)(?=\[)
  For loglevel (?<=\[)(.+)(?=\])
  ```
* Capture into a field:  `%{TIMESTAMP_ISO8601:datetime}` where `datetime` is a field name
* Full capture pattern:
  ```
  %{TIMESTAMP_ISO8601:datetime}%{SPACE}%{SPACE}-%{SPACE} (?<module>(?<= - )(.+)(?=\[))(\[)(?<loglevel>(.+)(?=\]))(\]: )%{GREEDYDATA:message}
  ```
* Transformed data \(1st log record\):    
  ```
  {
    "datetime": "2017-06-21 22:18:25,276",
    "module": "util.py",
    "loglevel": "DEBUG",
    "message": "2017-06-21 22:18:25,276 - util.py[DEBUG]: Reading from /proc/uptime (quiet=False)"
  }
  ```
* Configuration settings:
  ```
  filter {
    grok {
      match=> {
      "message"=>"%{TIMESTAMP_ISO8601:datetime}%{SPACE}%{SPACE}-%{SPACE} (?<module>(?<= - )(.+)(?=\[))(\[)(?<loglevel>(.+)(?=\]))(\]: )%{GREEDYDATA:message}"
    }
  }
  ```
* Invaluable tools: 
  * [grok constructor](http://grokconstructor.appspot.com/do/construction)
  * [grok debugger](http://grokdebug.herokuapp.com/)
  * [regex tester](https://regex101.com/)



