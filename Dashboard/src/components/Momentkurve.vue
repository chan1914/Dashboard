<template>
	<div id="chartdiv"></div>
</template>


<script>
	import * as am4core from "@amcharts/amcharts4/core";
	import * as am4charts from "@amcharts/amcharts4/charts";
	import am4themes_animated from "@amcharts/amcharts4/themes/animated";


	export default {
		name: 'Momentkurve',
		created() {

		},
		mounted() {
			am4core.ready(function () {

				// Themes begin
				am4core.useTheme(am4themes_animated);
				// Themes end

				// Create chart instance
				var chart = am4core.create("chartdiv", am4charts.XYChart);
				chart.paddingRight = 20;

				// Create axes
				var xAxis = chart.xAxes.push(new am4charts.CategoryAxis());
				xAxis.dataFields.label = "Milliseconds";

				var yAxis = chart.yAxes.push(new am4charts.ValueAxis())
				yAxis.dataFields.label = "NewtonMeter";

				// Create series
				var series = chart.data.series.push(new am4charts.LineSeries());
				series.dataFields.xAxis = "torque_log_values_id";
				series.dataFields.yAxis = "torque_values";
				series.tooltipText = "{torque_values}"
				

				// Make bullets grow on hover
				var bullet = series.bullets.push(new am4charts.CircleBullet());
				bullet.circle.strokeWidth = 2;
				bullet.circle.radius = 4;
				bullet.circle.fill = am4core.color("#f3e3c2");

				var bullethover = bullet.states.create("hover");
				bullethover.properties.scale = 1.3;



				//Datasets for momentkurve
				chart.data = [{
					"torque_log_values_id": 0,
					"torque_values": 0
				}, {
					"torque_log_values_id": 0,
					"torque_values": 5
				}, {
					"torque_log_values_id": 3,
					"torque_values": 20
				}, {
					"torque_log_values_id": 8,
					"torque_values": 40
				}, {
					"torque_log_values_id": 15,
					"torque_values": 70
				}, {
					"torque_log_values_id": 25,
					"torque_values": 63
				}, {
					"torque_log_values_id": 50,
					"torque_values": 35
				}, {
					"torque_log_values_id": 70,
					"torque_values": 23
				}, {
					"torque_log_values_id": 100,
					"torque_values": 14
				}];

			});
		}
	} // end am4core.ready()

</script>


<style>
	#chartdiv {
		width: 100%;
		height: 500px;
	}
</style>
