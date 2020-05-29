<template>
	<div id="app">
		
		<!--<Home msg="Hello world!" />-->
		<!--<CyklusTime></CyklusTime>-->
		<!--<SmoothLineTest></SmoothLineTest>-->
		<Momentkurve></Momentkurve>
		<!--<LineChart></LineChart>-->
		<!--<Histogramkurve></Histogramkurve>-->
		
		<!--<h3>Hej med dig</h3>
		<button class="btn waves-effect waves-light btn-large">
			Click me!
		</button>-->-->
	</div>
</template>

<script>
	import Home from './components/Home.vue'
	import LineChart from './components/LineChart.vue'
	import Momentkurve from './components/Momentkurve.vue'
	import CyklusTime from './components/CyklusTime.vue'
	import SmoothLineTest from './components/SmoothLineTest.vue'
	import Histogramkurve from './components/Histogramkurve.vue'

	export default {
		name: 'app',
		components: {
			Home,
			LineChart,
			Momentkurve,
			CyklusTime,
			SmoothLineTest,
			Histogramkurve
		}
	};
</script>

<style>
</style>

