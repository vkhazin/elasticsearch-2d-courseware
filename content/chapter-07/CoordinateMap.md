# Coordinate Map #

* Previously 'Tile Map'
* Possibly the most interesting visualization
* Requires mappings to be configured with geo_point type
* For previously populated log data cannot modify mapping for coordinates
* We will have to delete the indices created, re-create indices with mapping, and to re-populate data
* Shell script prepared for you
* Download and execute on the sandbox by running the following command:
```
bash <(curl -s https://s3.us-east-2.amazonaws.com/elasticsearch-courseware/sample-data/logMappings.sh)
```
* Go back to Visualize tab and select 'Tile map'
* Here it is a bit tricky - may need to go back to settings and refresh the fields
* Select 'Geo Coordinates' and select 'geo.coordinates' field
* Select 'green arrow' on top to apply changes and explore zoom in/out
* Switch to advanced options and check-out <a href="https://en.wikipedia.org/wiki/Web_Map_Service" target="_blank">wms</a>
* As versions of Kibana change the support for web map service works on and off
* There are <a href="https://www.elastic.co/elastic-tile-service" target="_blank">terms of service</a> for the tile service apparently separate from the elastic search product, go figure...