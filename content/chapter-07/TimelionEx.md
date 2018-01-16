# Timelion Exercise #

1. Access Kibana user interface with browser: http://ip-address:5601/
2. Select Timelion on the left hand navigation bar
3. Switch to full screen using the icon on the chart
4. In the formula area type: ```.es(*)```
5. Select time range of last 5 years
6. Select play button to update the presentation to present a typical time-series chart
7. Zoom-in to more active time period of the chart before next steps
8. In the formula area extend the expression to ```.es(*).derivative()```
9. Select '1h' for the time interval from drop-down list
10. And select the play button again - variation for number of events on hourly basis will be presented
11. Modify the formula: ```.es(*), .es(*,offset=-1h)``` to compare count of events to previous hour and select play button
12. Add some custom color to the time series: ```.es(*), .es(*,offset=-1h).color(yellow)``` and select play button
13. Convert line to bars: ```.es(*), .es(*,offset=-1h).bars().color(yellow)``` and select play button again
14. Add secondary data source to correlate number of events in log files to population of Israel: ```.es(*).bars(), .wbi(country=ISR).divide(100000)```
15. Adding another metric to the chart: ``` .es(), .es(metric=max:memory).divide(100)```
16. You are getting the rough idea of a potential...