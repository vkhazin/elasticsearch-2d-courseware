# Canvas Exercise

1. Install sample data provided by elastic by navigating to your instance [http://ipaddress:5601](http://ipaddress:5601)
2. Select `Canvas` link on the left-hand menu
3. Explorer existing canvas 
4. Select `Create workpad` -&gt; `Add element` -&gt; `Donut chart`
5. Select `Data` -&gt; `Change your data source` -&gt; `Elasticsearch sql query`:
   ```
   SELECT response.keyword FROM "kibana_sample_data_logs*"
   ```
6. Select `Display`
7. Under `Slice labels` select `Value` and `response.keyword`
8. Under `Slice angles` select `Count` and `response.keyword`
9. Feel free to add additional elements and/or to explore the sample `[Logs] Web Traffic`



