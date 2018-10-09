# Network Capacity #

* ElasticSearch is not sending too much data over the network
* But ElasticSearch is leveraging http(s) protocol, http2 seems to be still [work-in-process](https://github.com/elastic/elasticsearch/issues/10981)
* Number of sockets opened on the server, on the client, and on the network appliance could be a problem
* Server was alright since it listens on one port, the client running heavy batch job was not, it was getting saturated with the response sockets