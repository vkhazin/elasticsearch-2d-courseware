# Canvas Exercise

1. Install sample data provided by elastic by navigating to your instance [http://ipaddress:5601](http://ipaddress:5601)
2. Select `Canvas` link on the left-hand menu
3. Select `Create workpad` -&gt; `Add element` -&gt; `Donut chart`
4. Select `Data` -&gt; `Change your data source` -&gt; `Elasticsearch sql query`:
   ```
   SELECT clientip FROM "logstash*"
   ```
5. Select `Display`
6. Under `Slice labels` select `Value` and `clientip`
7. Under `Slice angles` select `Count` and `clientip`
8. Feel free to add additional elements and/or to explore the sample `[Logs] Web Traffic`



