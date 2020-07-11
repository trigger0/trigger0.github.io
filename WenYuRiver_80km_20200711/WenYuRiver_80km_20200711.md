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

# Wen Yu River at 2020-07-11

## Summary
Famous route, but still under construction. Because of that, the traffic is light but somehow inconvenient.

- Circumstance:
  - Weather is cloudy
  - Temperature is Suitable
  - A bit high humidity


- Planning:
  - Charging station inside the TongZhou canal park.
  - Shops near the TongZhou canal park.
  - A small town on the way, being removed.

- Road situation:
  - Specified lane not usable.
  - Main road is good but share with cars.
  - For now traffic is light, because the road still under construction.

## Personal Data

<style></style>
|           |                   | 2020-07-11 WenYu River |
| ---       | ---               | ---                    |
| GENERAL   | Type              | Ride                   |
|           | Distance          | 79.65 km               |
|           | Calorie           | 1886 kcal              |
|           | Activity ID       | #83657863              |
| SPEED     | Avg Moving Speed  | 18.76 km/h             |
|           | Avg Speed         | 16.16 km/h             |
|           | Max Speed         | 34.97 km/h             |
| ELEVATION | Elevation Gain    | 341 m                  |
|           | Elevation Loss    | 334 m                  |
|           | Min-Max Elevation | -4.26-56.83m           |
|           | Min-Max Gradient  | -20-20                 |
| DURATION  | Moving            | 4:14:45                |
|           | Total             | 4:55:44                |
|           | Start             | 2020-07-11 12:24       |
|           | End               | 2020-07-11 17:20       |

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
			url: "WenYuRiver_80km_20200711.gpx",
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
