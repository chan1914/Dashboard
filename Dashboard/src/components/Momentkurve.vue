<template>
	<div id="chartdiv"></div>
</template>


<script>
	import * as am4core from "@amcharts/amcharts4/core";
	import * as am4charts from "@amcharts/amcharts4/charts";
	import am4themes_animated from "@amcharts/amcharts4/themes/animated";


	export default {
		name: 'Momentkurve',
		mounted() {
			am4core.ready(function () {

				// Themes begin
				am4core.useTheme(am4themes_animated);
				// Themes end

				// Create chart instance
				var chart = am4core.create("chartdiv", am4charts.XYChart);
				//chart.paddingRight = 20;

				// Chart data external
				chart.dataSource.url = "https://raw.githubusercontent.com/chan1914/Dashboard/master/Dashboard_data%20-%20csv.csv";
				chart.dataSource.parser = new am4core.CSVParser();
				chart.dataSource.parser.options.useColumnNames = true;

				chart.data = [{
					"torque_log_values_id": "1",
					"torque_values": 501
				}, {
					"torque_log_values_id": "2",
					"torque_values": 301
				}, {
					"torque_log_values_id": "3",
					"torque_values": 201
				}, {
					"torque_log_values_id": "3",
					"torque_values": 165
				}, {
					"torque_log_values_id": "4",
					"torque_values": 139
				}, {
					"torque_log_values_id": "5",
					"torque_values": 128
				}, {
					"torque_log_values_id": "6",
					"torque_values": 99
				}, {
					"torque_log_values_id": "7",
					"torque_values": 60
				}, {
					"torque_log_values_id": "2",
					"torque_values": 50
				}];

				// Create axes
				var idAxis = chart.xAxes.push(new am4charts.ValueAxis());
				idAxis.dataFields = "torque_log_values_id";
				idAxis.title.text = "Miliseconds";
				idAxis.renderer.grid.template.location = 0.5;
				idAxis.startLocation = 0.5;
				idAxis.endLocation = 0.5;
				idAxis.min = 0;
				idAxis.max = 10;


				var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
				valueAxis.dataFields = "torque_values";
				valueAxis.title.text = "NewtonMeter";

				// Create series
				var series1 = chart.data.series.push(new am4charts.LineSeries());
				series1.dataFields.valueY = "torque_values";
				series1.dataFields.valueX = "torque_log_values_id";
				series1.bullets.push(new am4charts.CircleBullet());

				// Add legend
				chart.legend = new am4charts.Legend();

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
