# Timelion Exercise

1. Access Kibana user interface with browser: [http://ip-address:5601/](http://ip-address:5601/)
1. Select Visualization and then search for Timelion
1. Switch to full screen using the icon on the chart
1. In the formula area type: `.es(*)`
1. Select a time range of the last 2 years
1. Select the play button to update the presentation to present a typical time-series chart
1. Zoom-in to a more active time period of the chart before the next steps
1. In the formula area, extend the expression to `.es(*).derivative()`
1. Select '1h' for the time interval from the drop-down list
1. And select the play button again - variation for the number of events on an hourly basis will be presented
1. Add some custom color to the time series: `.es(*).color(yellow)` and select the play button
1. Convert line to bars: `.es(*).bars().color(red)` and select play button again
1. Adding another metric to the chart: `.es(),.es(metric=max:memory).divide(100)`
1. Can add data from a World Bank, e.g. world population in billions:
     `.es(),.wbi(indicator=SP.POP.TOTL).divide(10000000)`
1. The world bank indicators may experience intermittent issues when querying and may stop working over time
1. You are getting the idea of a potential...
