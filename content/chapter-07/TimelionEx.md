# Timelion Exercise

1. Access Kibana user interface with browser: [http://ip-address:5601/](http://ip-address:5601/)
2. Select Visualization and then search for Timelion
3. Switch to full screen using the icon on the chart
4. In the formula area type: `.es(*)`
5. Select a time range of the last 2 years
6. Select the play button to update the presentation to present a typical time-series chart
7. Zoom-in to a more active time period of the chart before the next steps
8. In the formula area, extend the expression to `.es(*).derivative()`
9. Select '1h' for the time interval from the drop-down list
10. And select the play button again - variation for the number of events on an hourly basis will be presented
11. Modify the formula: `.es(*), .es(*,offset=-1h)` to compare the count of events to the previous hour 
12. Add some custom color to the time series: `.es(*), .es(*,offset=-1h).color(yellow)` and select the play button
13. Convert line to bars: `.es(*), .es(*,offset=-1h).bars().color(yellow)` and select play button again
14. Adding another metric to the chart: `.es(), .es(metric=max:memory).divide(100)`
15. Can add data from a World Bank, e.g. world population in billions:
     `.es(),.wbi(indicator=SP.POP.TOTL).divide(10000000)`
16. You are getting the idea of a potential...



