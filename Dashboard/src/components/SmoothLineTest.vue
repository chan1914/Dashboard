<template>
	<div id="chartdiv"></div>
</template>

<script>
	import * as am4core from "@amcharts/amcharts4/core";
	import * as am4charts from "@amcharts/amcharts4/charts";
	import am4themes_animated from "@amcharts/amcharts4/themes/animated";

	am4core.useTheme(am4themes_animated);

	export default {
		name: 'Home',
		mounted() {
			let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);
			chart.paddingRight = 20;

		// Create axes
		var durationAxis = chart.xAxes.push(new am4charts.DurationAxis(Number));
		durationAxis.dataFields.category = "time";
		durationAxis.renderer.minGridDistance = 50;
		durationAxis.renderer.grid.template.location = 0.5;
		durationAxis.startLocation = 0.5;
		durationAxis.endLocation = 0.5;

		// Create value axis
		var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
		valueAxis.baseValue = 0;

		// Create series
		var series = chart.series.push(new am4charts.LineSeries());
		series.dataFields.valueY = "value";
		series.dataFields.categoryX = "time";
		series.strokeWidth = 2;
		series.tensionX = 0.77;

		var range = valueAxis.createSeriesRange(series);
		range.value = 0;
		range.endValue = -1000;
		range.contents.stroke = am4core.color("#FF0000");
		range.contents.fill = range.contents.stroke;

		// Add scrollbar
		var scrollbarX = new am4charts.XYChartScrollbar();
		scrollbarX.series.push(series);
		chart.scrollbarX = scrollbarX;

		chart.cursor = new am4charts.XYCursor();
	}
	}
</script>

<style scoped>
	#chartdiv {
		width: 100%;
		height: 500px;
	}
</style>