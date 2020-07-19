<head>
	<title>leaflet-elevation.js</title>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	<meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
	<style>
		html,
		body,
		.leaflet-map,
		.elevation-div {
			height: 100%;
			width: 100%;
			padding: 0px;
			margin: 0px;
		}

		.leaflet-map {
			height: 55%;
			max-height: 100vh;
			min-height: 600px;
		}

		.elevation-div {
			height: 25%;
			font: 12px/1.5 "Helvetica Neue", Arial, Helvetica, sans-serif;
		}
	</style>

	<!-- leaflet-ui -->
	<script src="https://unpkg.com/leaflet@1.3.2/dist/leaflet.js"></script>
	<script src="https://unpkg.com/leaflet-ui@0.2.5/dist/leaflet-ui.js"></script>

	<!-- leaflet-elevation -->
	<link rel="stylesheet" href="https://unpkg.com/@raruto/leaflet-elevation@1.3.0/dist/leaflet-elevation.min.css" />
	<script src="https://unpkg.com/@raruto/leaflet-elevation@1.3.0/dist/leaflet-elevation.min.js"></script>

</head>

# JiuDu River at 2020-07-19

## Summary
- Sunny day but forgot to take long sleeve, Got sunburned.
- Under estimate the intensity of climbing. It's not just a 75km route, and also 600m climbing.

Circumstance:
- It's a sunny day.
- Temperature is high (35°C).

Planning:
- Charging station (国家电网充电站 北武路) is good, but only 2 stakes.
- Total distance is 75km.
- Small village along the way. Plenty depots.
- No restaurant found, maybe because of the COVID-19. Need to take some food.

The road situation:
- About 5km HuaiChang Road (怀昌路), very crowded and share with cars and large trucks.
- Once into the moutain, road situation become way more better. Still share with cars but traffic is light.
- After moutain road is HuaiChang Road (怀长路), there is bike only road. Flat like a high way, but very few shady place.

## Personal Data

<style></style>
|           |                   | 2020-07-19 75km  |
|-----------|-------------------|------------------|
| GENERAL   | Type              | Ride             |
|           | Distance          | 74.72            |
|           | Calorie           | 1756 kcal        |
|           | Activity ID       | #84112677        |
| SPEED     | Avg Moving Speed  | 18.89 km/h       |
|           | Avg Speed         | 18.10 km/h       |
|           | Max Speed         | 47.35 km/h       |
| ELEVATION | Elevation Gain    | 612 m            |
|           | Elevation Loss    | 611 m            |
|           | Min-Max Elevation | 52.02-396.92 m   |
|           | Min-Max Gradient  | -19%-20%         |
| DURATION  | Moving            | 3:57:21          |
|           | Total             | 4:07:40          |
|           | Start             | 2020-07-19 08:17 |
|           | End               | 2020-07-19 12:25 |


## Route Book
<div id="map" class="leaflet-map"></div>
<script>
	var opts = {
		map: {
			center: [41.4583, 12.7059],
			zoom: 5,
			fullscreenControl: false,
			resizerControl: true,
		},
		elevationControl: {
			url: "JiuDuRiver_75km_20200719.gpx",
			options: {
				theme: "lightblue-theme",
				collapsed: false,
				detached: true,
				summary: "multiline",
			},
		},
		layersControl: {
			options: {
				collapsed: false,
			},
		},
	};

	var map = new L.Map('map', opts.map);

	var controlElevation = L.control.elevation(opts.elevationControl.options);
	var controlLayer = L.control.layers(null, null, opts.layersControl.options);

	controlElevation.addTo(map);
	controlElevation.load(opts.elevationControl.url);

	map.on('eledata_loaded', function(e) {
		if (!controlLayer._map) controlLayer.addTo(map);
		controlLayer.addOverlay(e.layer, e.name);
	});
</script>
