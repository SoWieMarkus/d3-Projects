<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        body {
            font-family: "Helvetica Neue", Helvetica, sans-serif;
            font-size: 14px;
            color: #333;
        }

    </style>

    <!-- Load d3.js -->
    <script src="https://d3js.org/d3.v4.js"></script>
    <script src="https://d3js.org/d3-scale-chromatic.v1.min.js"></script>
    <script src="https://d3js.org/d3-geo-projection.v2.min.js"></script>
</head>
<body>

<!-- Create an element where the map will take place -->
<span id="Auswahl"></span>
<br>


<script>

    let backgroundColor = "none"
    let hoverColor = "blue"
    let fillColor = "steelblue"
    let borderColor = "white"
    let borderHoverColor = "white"
    let borderWidth = "0.5px"
    let width = 500;
    let height = 300;

    d3.select("body").append("svg").attr("width", "500").attr("height", "300").attr("id", "my_dataviz")

    let svg = d3.select("svg");

    let path = d3.geoPath();
    let projection = d3.geoMercator()
        .scale(7000)
        .center([13.458333, 50.929472])
        .translate([width / 2, height / 2]);

    svg.append("rect")
        .attr("width", "100%")
        .attr("height", "100%")
        .attr("fill", backgroundColor);

    let div = d3.select("body").append("div")
        .attr("class", "tooltip")
        .style("opacity", 0);

    let data = d3.map();
    let colorScale = d3.scaleThreshold()
        .domain([100000, 1000000, 10000000, 30000000, 100000000, 500000000])
        .range(d3.schemeBlues[7]);

    d3.queue()
        .defer(d3.json, "landkreise.geojson")
        .await(ready);

    function ready(error, topo) {

        let mouseOver = function (d) {
            d3.selectAll(".Country").attr("fill", fillColor)
            if (d.properties.link === null) return;
            d3.select(this).attr("fill", hoverColor).style("stroke", borderHoverColor)
        }

        let mouseLeave = function (d) {
            d3.selectAll(".Country").attr("fill", fillColor);
            d3.select(this).attr("fill", fillColor).style("stroke", borderColor)
        }

        svg.append("g")
            .selectAll("path")
            .data(topo.features)
            .enter()
            .append("path")
            .attr("d", d3.geoPath().projection(projection))
            .attr("pointer-events", "visible")
            .attr("fill", fillColor)
            .attr("cursor", function (d) {
                if (d.properties.link === null) return "no-drop";
                return "pointer";
            })
            .style("stroke", borderColor)
            .style("stroke-width", borderWidth)
            .attr("class", function (d) {
                return "Country"
            })
            .style("opacity", 1)
            .on("mouseover", mouseOver)
            .on("mouseleave", mouseLeave)
            .on("click", function (d) {
                if (d.properties.link === null) return;
                window.location.href = window.location.href += d.properties.link;
            })
    }

</script>

</body>
</html>
