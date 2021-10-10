# Preview
https://sowiemarkus.github.io/interactive-map

# Motivation

I programmed this prototype for a customer. This customer had locations in various districts in the state of Saxony (Germany) which the users of his website should be able to access using this map.

# Functionalty

## 1. GeoJSON Daten

<a href="https://de.wikipedia.org/wiki/GeoJSON">GeoJSON</a> is a format in which geographical objects are represented in a JSON format. This data will be the basis for the map. There are several ways to get the relevant data. For one, you can create / convert them yourself using a tool like ArcGIS. However, some data sources are also available online (OpenStreetMap, <a href="http://opendatalab.de/projects/geojson-utilities/">OpenDataLab</a>). If the data is not in GeoJSON format, it is also possible to convert it online (see <a href="https://mygeodata.cloud/converter/shp-to-geojson">here</a>).

However, this data can still show errors. D3.js expects the data of the polygon in clockwise direction. Otherwise the polygons are displayed inverted, as discussed  <a href="https://stackoverflow.com/questions/47234805/d3-v4-geo-draws-boundary-inverted">here</a>. If this is the case, the coordinates can be edited accordingly using <a href="https://observablehq.com/@bumbeishvili/rewind-geojson">this tool</a>.


