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

# Yan Qi Lake at 2020-06-25

## Summary
Comfortable circumstance, distance not very long, also very bike-friendly.

Circumstance:
- Weather is cloudy
- Temperature is Suitable 

Planning:
- Not a long route, about 22km per loop. So I ride for 2 loops.
- A vending machine near the Kempinski.
- A KFC on the way.

Road situation:
- Specified lane for bikes mostly.
- Traffic is light.

## Personal Data

<style></style>
|           |                   | 2020-06-25 YanQi Lake |
| ---       | ---               | ---                   |
| GENERAL   | Type              | Ride                  |
|           | Distance          | 44.31 km              |
|           | Calorie           | 1016 kcal             |
|           | Activity ID       | #82722360             |
| SPEED     | Avg Moving Speed  | 18.50 km/h            |
|           | Avg Speed         | 15.47 km/h            |
|           | Max Speed         | 48.30 km/h            |
| ELEVATION | Elevation Gain    | 325 m                 |
|           | Elevation Loss    | 327 m                 |
|           | Min-Max Elevation | 52.98-138.83m         |
|           | Min-Max Gradient  | -17%-19%              |
| DURATION  | Moving            | 2:23:42               |
|           | Total             | 2:51:55               |
|           | Start             | 2020-06-25 10:40      |
|           | End               | 2020-06-25 13:32      |

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
			url: "YanQiLake_44km_20200625.gpx",
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
