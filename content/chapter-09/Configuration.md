# Configuration #

* Review node types, number of shards, and number of replicas
* With heavy loads master nodes, client nodes, and data nodes maybe best separate
* Log location vs. data location
* Data volumes - encrypted or not
* ElasticSearch defaults to anonymous read/write enabled access
* Maybe you don't want your cluster on [this list](https://www.shodan.io/search?query=elasticsearch+%27You+Know%2C+for+Search%27)
* Network protection anyone?
* Don't trust humans - automate configuration and deployment