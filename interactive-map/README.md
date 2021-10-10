# Preview
https://sowiemarkus.github.io/interactive-map

# Motivation

Diesen Prototypen habe ich für einen Kunden programmiert. Dieser Kunde hatte in verschiedenen Landkreisen im Bundesland Sachsen (Deutschland) Standorte, auf welche die Nutzer seiner Webseite mittels dieser Karte zugreifen sollen können.

# Funktionsweise

## 1. GeoJSON Daten

<a href="https://de.wikipedia.org/wiki/GeoJSON">GeoJSON</a> ist ein Format, in welchem geografische Objekte in einem JSON Format dargestellt werden. Diese Daten werden die Grundlage für die Karte sein. Es gibt verschiedene Möglichkeiten, die entsprechenden Daten zu erhalten. Zum einen kann man sie selbst mit Hilfe eines Tools wie ArcGIS erstellen / konvertieren. Online sind jedoch auch einige Datenquellen vorhanden (OpenStreetMap, <a href="http://opendatalab.de/projects/geojson-utilities/">OpenDataLab</a>. Sollten die Daten nicht im GeoJSON Format vorliegen, gibt es ebenfalls die Möglichkeit diese Online zu konvertieren (sh. <a href="https://mygeodata.cloud/converter/shp-to-geojson").

Diese Daten können jedoch immer noch Fehler ausweisen. D3.js erwartet die Daten der Polygon im Uhrzeigersinn. Sonst werden die Polygone invertiert angezeigt, wie <a href="https://stackoverflow.com/questions/47234805/d3-v4-geo-draws-boundary-inverted">hier</a> diskutiert. Sollte dies der Fall sein, können die Koordinaten mit Hilfe <a href="https://observablehq.com/@bumbeishvili/rewind-geojson">dieses Tools</a> entsprechend bearbeitet werden.
