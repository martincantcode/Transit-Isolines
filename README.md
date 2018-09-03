# Transit-Isolines
Create visualisations of public transport isochrones using here.coms API and QGIS

1. Register for a freemium account at developer.here.com to get an API key and app id.
2. Enter the following request to get an xml file of all stations within X minutes travel time. Replace all parameters according to your own project: app code, app id, center (use google maps to get X and Y coordinates for your point of origin), time, maxDur (duration of travel up to 90 minutes), max_change, and timespan.
https://transit.api.here.com/v3/isochrone?app_id=[your_app_id]&app_code=[your_app_code]&center=52.521780,13.413407&time=2018-08-31T09:00:00&maxDur=60&max_change=3&timespan=60
3. Save xml
4. replace xml filename and target csv filename in the Python Script and run.
5. Open csv in Excel or Numbers, calculate remaining walking time in an extra column. Name that column "walk".
6. Open QGIS. Load a basemap you like. Then add the csv via a new delimited text layer.
7. Now comes the fun part. Styling! Go to layer properties and make size a function of the remaining walking time. I used ("walk" ) * 80+10. Assuming you walk at 80 meters per minute (a very conservative guess). The +10 is there so stations with zero walking time remaining will still show up on the map. Don't forget to set your units to map units. And then have fun playing with colors and opacity until it looks the way you want it to.
