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

# Yan Qi Lake small loop at 2020-07-05

## Summary
Along with @WenXue Qin

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
			url: "YanQiLake_10km_20200705.gpx",
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
