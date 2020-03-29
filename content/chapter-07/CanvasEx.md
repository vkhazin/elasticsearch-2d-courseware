# Canvas Exercise

1. Install sample data provided by elastic by navigating to your instance [http://ipaddress:5601](http://ipaddress:5601)
2. Select `Load a data set and a Kibana dashboard`
3. Select `Sample web logs`
4. Proceed to `Discover` link on the left hand
5. Familiarize yourself with json structure of the sample data loaded
6. Select `Canvas` link on the left-hand menu
7. Select `Create workpad` -&gt; `Add element` -&gt; `Donut chart`
8. Select `Data` -&gt; `Change your data source` -&gt; `Elasticsearch sql query`:
   ```
   SELECT response.keyword FROM "kibana_sample_data_logs*"
   ```
9. Select `Display`
10. Under `Slice labels` select `Value` and `response.keyword`
11. Under `Slice angles` select `Count` and `response.keyword`
12. Feel free to add additional elements and/or to explore the sample `[Logs] Web Traffic`



