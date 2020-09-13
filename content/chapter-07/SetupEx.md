# Exercise: Setup Kibana

1. Log-in into your sand-box
1. Double-check elastic search service is running:
   ```
   sudo systemctl start elasticsearch
   ```
1. From terminal download and install Public Signing Key, **not required** as we have done it before:
   ```
   curl https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
   ```
1. From terminal add repository definitions, **not required** as we have done it before:
   ```
   echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | \
       sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list %% \
       sudo apt-get update
   ```
1. Update repositories and install Kibana:
   ```
   sudo apt-get install kibana
   ```
1. Populate sample data, it will take a couple of** minutes** to finish:
   ```
   cd ~/
   curl -O https://s3.us-east-2.amazonaws.com/elasticsearch-courseware/sample-data/logs.json
   curl  -XPOST 'localhost:9200/_bulk' \
      -H 'content-type: application/json' \
      --data-binary "@logs.json"
   ```
1. By default, Kibana listens to localhost and it won't be really helpful in most environments
1. Edit kibana.yml to modify the following line: `server.host: 0.0.0.0`
   ```
   sudo nano /etc/kibana/kibana.yml
   ```
1. Start Kibana service:
    ```
    sudo systemctl start kibana
    ```
1. Open browser to [http://ip-address:5601](http://ip-address:5601), where ip address is the same as for ssh connection
1. Select 'Explore your own data' option 
1. Kibana requires configuration before it can display data: look for 'Index Patterns', it keeps moving between releases
1. To find out what indices we have in the cluster:
    ```
    curl localhost:9200/_cat/indices
    ```
1. You can also see them listed below the `Index Pattern` field
1. After typing the index name pattern with a star proceed to the next step
1. Kibana, by default, requires a date-time field to filter data on
1. By default, Kibana displays data for the last 15 minutes and in a simulated environment it is often an empty result set
1. Look at the top-right corner to adjust the timeframe to 5 years
1. You should be able to see some data now, if not, common troubles are index pattern configuration and a timeframe selection
1. There is a star icon or a maybe another way in the future version to set the index pattern as a default
1. Head to the `Discover` link on the left
1. Adjust time-frame in the top-right corner to `last 5 years`
1. Use the search box to locate some record using KQL syntax: `bytes > 0` or [legacy Lucene syntax](https://www.elastic.co/guide/en/kibana/current/lucene-query.html): `extension:gif`
1. Select the `add` link next to few fields to present selected fields on the results pane
1. Select any record and switch between Text and Json views
1. Save search using the link on top of the page
1. Get comfortable with running Lucene syntax queries using the search box - you are going to need it moving forward
1. Notice the drill-down capabilities using the chart on the top of the page using a mouse
1. We will look into other links a bit later...



