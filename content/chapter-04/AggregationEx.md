# Aggregation Exercise #

* Log-in into your ElasticSearch sandbox
* Make sure elastic search is running:
```
sudo service elasticsearch restart
```
* Populate few sample movie data:
```
curl -O https://s3.us-east-2.amazonaws.com/elasticsearch-courseware/sample-data/movies.txt
curl -XPOST 'localhost:9200/_bulk' -H 'content-type: application/json' --data-binary "@movies.txt"
```
* Confirm there are some records to search on:
```
curl 'localhost:9200/movies/movies/_search?pretty=true'
```
* Let's aggregate on actor name
```
curl -XPOST 'localhost:9200/movies/movies/_search?pretty=true' \
  -H 'content-type:application/json' \
  -d '
{
  "size": 0,
  "aggs": {
    "actor_name": {
      "terms": {
        "field": "Starring.CastCrewName.keyword"
      }
    }
  }
}'
```
* What buckets did you get?
* How do I get more than 10 buckets? [Check StackOverflow posting!](http://stackoverflow.com/questions/22927098/show-all-elasticsearch-aggregation-results-buckets-and-not-just-10)
* What is 'sum_other_doc_count' field?
* Let's find out average movie rating for the actor:
```
curl -XPOST 'localhost:9200/movies/movies/_search?pretty=true' \
  -H 'content-type:application/json' \
  -d '
{
  "size": 0,
  "aggs": {
    "actor_name": {
      "terms": {
        "field": "Starring.CastCrewName.keyword"
      },
      "aggs": {
        "rating": {
          "avg": {
            "field": "StarRating"
          }
        }
      }
    }
  }
}
'
```
* Take a moment to understand the variety of [aggregation types](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html)
* Pick an aggregation we did not cover in the slides and make it work