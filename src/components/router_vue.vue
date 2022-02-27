<template>
	<STM32F1Board/>
	<control_panel/>
</template>


<script>
	import STM32F1Board from "./boards/STM32F1Board.vue";
	import control_panel from "./utils/control_panel.vue";
	//import ArduinoBoard from "./boards/Arduino.vue";

	export default {
		components: {
			STM32F1Board,
			control_panel,
		}	
	}
</script>



<style>

</style>
