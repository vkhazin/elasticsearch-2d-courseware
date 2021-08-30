# Canvas Exercise

1. Navigate to your instance [http://ipaddress:5601](http://ipaddress:5601)
2. Select `Canvas` link on the left-hand menu
3. Select `Create workpad -> Add element -> Chart -> Pie`
4. Select `Data -> Change your data source -> Elasticsearch SQL`:
   ```
   SELECT clientip,
   count(1) FROM "logstash*"
   GROUP BY clientip
   ORDER BY count(1) DESC
   LIMIT 10
   ```
5. Select `Display`
6. For `Slice labels` select `Value` and `clientip`
1. For `Slice Angles` select `Value` and `count`
7. Feel free to add additional elements and/or to explore the sample `[Logs] Web Traffic`
