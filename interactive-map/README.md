# Preview
https://sowiemarkus.github.io/interactive-map

# Motivation

I programmed this prototype for a customer. This customer had locations in various districts in the state of Saxony (Germany) which the users of his website should be able to access using this map.

# Functionalty

## 1. GeoJSON Data

<a href="https://de.wikipedia.org/wiki/GeoJSON">GeoJSON</a> is a format in which geographical objects are represented in a JSON format. This data will be the basis for the map. There are several ways to get the relevant data. For one, you can create / convert them yourself using a tool like ArcGIS. However, some data sources are also available online (OpenStreetMap, <a href="http://opendatalab.de/projects/geojson-utilities/">OpenDataLab</a>). If the data is not in GeoJSON format, it is also possible to convert it online (see <a href="https://mygeodata.cloud/converter/shp-to-geojson">here</a>).

However, this data can still show errors. D3.js expects the data of the polygon in clockwise direction. Otherwise the polygons are displayed inverted, as discussed  <a href="https://stackoverflow.com/questions/47234805/d3-v4-geo-draws-boundary-inverted">here</a>. If this is the case, the coordinates can be edited accordingly using <a href="https://observablehq.com/@bumbeishvili/rewind-geojson">this tool</a>.

## 2. D3.js

With the JavaScript library d3.js, a map can now simply be built from this geographic data. You can check out my code in for this. However, for your card to work properly, you will need to make some changes on your own.

### Configure the center of the map

Change the scale and the center of the projection.

```javascript
let projection = d3.geoMercator()
        .scale(7000)
        .center([13.458333, 50.929472])
        .translate([width / 2, height / 2]);
```

### Edit onClick

```javascript
.on("click", function (d) {
                if (d.properties.link === null) return;
                window.location.href = window.location.href += d.properties.link;
            })
```

### Style the map

```javascript
let backgroundColor = "none"
let hoverColor = "blue"
let fillColor = "steelblue"
let borderColor = "white"
let borderHoverColor = "white"
let borderWidth = "0.5px"
let width = 500;
let height = 300;
```



