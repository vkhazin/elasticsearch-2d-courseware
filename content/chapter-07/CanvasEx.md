# Canvas Exercise

1. Install sample data provided by elastic by navigating to your instance http://ipaddress:5601
1. Select `Load a data set and a Kibana dashboard`
1. Select `Sample web logs`
1. Proceed to `Discover` link on the left hand
1. Familiarize yourself with json structure of the sample data loaded
1. Select `Canvas` link on the left-hand menu
1. Select `Create workpad` -> `Add element` -> `Donut chart`
1. Select `Data` -> `Change your data source` -> `Elasticsearch sql query`:
```
SELECT response.keyword FROM "kibana_sample_data_logs*"
```
1. Select `Display`
1. Under `Slice labels` select `Value` and `response.keyword`
1. Under `Slice angles` select `Count` and `response.keyword`
1. Feel free to add additional elements and/or to explore the sample `[Logs] Web Traffic`
