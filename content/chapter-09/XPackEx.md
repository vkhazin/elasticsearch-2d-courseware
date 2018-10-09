# XPack Exercise #

1. Stop ElasticSearch and Kibana, or installation may **fail**:
```
sudo service kibana stop && sudo service elasticsearch stop
```
2. Installing X-Pack plug-in for ElasticSearch:
```
cd /usr/share/elasticsearch/
sudo ./bin/elasticsearch-plugin install x-pack
```
3. Install X-Pack plug-in for Kibana (will take quite some time):
```
cd /usr/share/kibana/
sudo ./bin/kibana-plugin install x-pack
```
4. Start ElasticSearch and Kibana services:
```
sudo service elasticsearch start && sudo service kibana start
```
5. Generate passwords:
```
cd /usr/share/elasticsearch/bin/x-pack/
sudo ./setup-passwords interactive
```
6. User the same password for all users: ```changeme```
7. Modify /etc/kibana/kibana.yml:
```
sudo nano /etc/kibana/kibana.yml
```
8. Values to change:
```
elasticsearch.username: "elastic"
elasticsearch.password: "changeme"
```
9. Restart Kibana service: `sudo service kibana restart`
10. Navigate to http://ip-address:5601
11. Login with default credentials: elastic/changeme
12. Explore the 'Monitoring' and 'Management' links