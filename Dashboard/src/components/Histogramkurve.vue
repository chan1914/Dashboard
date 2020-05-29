<template>
	<div id="chartdiv"></div>
</template>
	

<script>
	import * as am4core from "@amcharts/amcharts4/core";
	import * as am4charts from "@amcharts/amcharts4/charts";
	import am4themes_animated from "@amcharts/amcharts4/themes/animated";

	am4core.useTheme(am4themes_animated);

	export default {
		name: 'Histogram',
		mounted() {

			// Create chart instance
			var chart = am4core.create("chartdiv", am4charts.XYChart);

			// Add data
			chart.data = [{
				"country": 0,
				"visits": 0
			}, {
				"country": 70,
				"visits": 80
			}, {
				"country": 100,
				"visits": 270
			}, {
				"country": 150,
				"visits": 225
			}, {
				"country": 175,
				"visits": 310
			}, {
				"country": 200,
				"visits": 60
			}, {
				"country": 260,
				"visits": 50
			}, {
				"country": 275,
				"visits": 75
			}, {
				"country": 365,
				"visits": 175
			}, {
				"country": 400,
				"visits": 0
			}, {
				"country": 500,
				"visits": 5
			}];

			// Create axes

			var categoryAxis = chart.xAxes.push(new am4charts.CategoryAxis());
			categoryAxis.dataFields.category = "country";
			categoryAxis.renderer.grid.template.location = 0;
			categoryAxis.renderer.minGridDistance = 30;

			categoryAxis.renderer.labels.template.adapter.add("dy", function (dy, target) {
				if (target.dataItem && target.dataItem.index & 2 == 2) {
					return dy + 25;
				}
				return dy;
			});

			var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
			valueAxis.dataFields.category = "visits";

			// Create series
			var series = chart.series.push(new am4charts.ColumnSeries());
			series.dataFields.valueY = "visits";
			series.dataFields.categoryX = "country";
			series.name = "Visits";
			series.columns.template.tooltipText = "{categoryX}: [bold]{valueY}[/]";
			series.columns.template.fillOpacity = .8;

			var columnTemplate = series.columns.template;
			columnTemplate.strokeWidth = 2;
			columnTemplate.strokeOpacity = 1;

		}
	}
</script>

<style scoped>
	#chartdiv {
		width: 100%;
		height: 500px;
	}
</style>


