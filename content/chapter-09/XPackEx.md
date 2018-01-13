# XPack Exercise #

* Stop ElasticSearch and Kibana, or installation may fail!:
```
sudo service kibana stop && sudo service elasticsearch stop
```
* Installing X-Pack plug-in for ElasticSearch:
```
cd /usr/share/elasticsearch/
sudo ./bin/elasticsearch-plugin install x-pack
```
* Install X-Pack plug-in for Kibana (will take quite some time):
```
cd /usr/share/kibana/
sudo ./bin/kibana-plugin install x-pack
```
* Generate passwords:
```
cd /usr/share/elasticsearch/bin/x-pack/
sudo ./setup-passwords interactive
```
* User the same password for all users: ```changme```
* Modify /etc/kibana/kibana.yml:
```
sudo nano /etc/kibana/kibana.yml
```
* Values to change:
```
elasticsearch.username: "elastic"
elasticsearch.password: "changeme"
```
* Start ElasticSearch and Kibana services:
```
sudo service elasticsearch start && sudo service kibana start
```
* Navigate to http://ip-address:5601
* Login with default credentials: elastic/changeme
* Explore the 'Monitoring' and 'Management' links
* Feel free to install other monitoring plug-ins to find out which one you like the most
* Links provided on the previous slide...