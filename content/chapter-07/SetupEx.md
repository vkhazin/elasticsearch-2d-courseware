# Exercise: Setup Kibana #

1. Log-in into your sand-box
2. Double check elasticsearch service is running:
```
sudo service elasticsearch start
```
3. From terminal download and install Public Signing Key:
```
curl https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
4. From terminal add repository definitions:
```
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
```
5. Update repositories info and install Kibana:
```
sudo apt-get update && sudo apt-get install kibana
```
6. Start Kibana service:
```
sudo service kibana start
```
7. Populate sample data:
```
cd ~/
curl -O https://s3.us-east-2.amazonaws.com/elasticsearch-courseware/sample-data/logs.json
curl  -XPOST 'localhost:9200/_bulk' \
      -H 'content-type: application/json' \
      --data-binary "@logs.json"
```
8. By default Kibana listens to localhost and it won't be really helpful in most environments
9. Edit kibana.yml to modify following line: ```server.host: 0.0.0.0```
```
sudo nano /etc/kibana/kibana.yml
```
10. Restart Kibana service:
```
sudo service kibana restart
```
11. Open browser to http://ip-address:5601, where ip address is the same as for ssh connection
12. Kibana requires configuration before it can display data: look for 'Index Patterns', it keeps moving between releases
13. To find out what indices we have in the cluster:
```
curl localhost:9200/_cat/indices
```
14. You can also see them listed below the 'Index Pattern' field
15. After typing index name pattern with a star proceed to the next step
16. Kibana (by default) requires a date-time field to filter data on
17. By default Kibana displays data for the last 15 minutes and in a simulated environment it is often an empty result set
18. Look at the top-right corner to adjust the timeframe
19. You should be able to see some data now, if not, common troubles are index pattern configuration and a timeframe selection
20. There is a star icon or a maybe another way in the future version to set index pattern as a default
21. Head to the 'Discover' link on the left
22. Adjust time-frame in the top-right corner to 'last 5 years'
23. Use search box to locate some record
24. Select 'add' link next to few fields to present selected fields on the results pane
25. Select any record and switch between text and json views
26. Save search using link on top of the page
27. Get comfortable with running Lucene syntax queries using the search box - you are going to need it moving forward
28. Notice the drill down capabilities using the chart on the top of the page using a mouse
29. We will look into other links a bit later...