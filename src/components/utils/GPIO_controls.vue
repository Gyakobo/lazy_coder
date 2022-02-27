<template>
	<div class="control_panel_gpio">
		<div id="banner">
			<p> Name </p>
		</div>
		
		<div id="controls">
			<modes_vue/>
			<modes_vue/>
		</div>
	</div>

</template>



<script>
import modes_vue from "./modes_vue.vue";

export default {
	components: {
		modes_vue,
	}
}

</script>



<style>
	.control_panel_gpio {
		position:	relative;

		padding:	0;
		margin:		0;

		top:		0;

		width:		100%;

		min-height:	9rem;
		max-height:	16rem;

		/*border-bottom:	1px solid gray;*/

		margin-bottom:	5px;

	}

	#banner {
		position:	absolute;

                top:                    0;  
                    
                padding:                0;  
                margin:                 0;  
                    
                width:                  100%;
                height:                 30px;

                box-shadow:             0px 6px 15px rgba(0, 0, 0, 0.25), 0px -6px 15px rgba(0, 0, 0, 0.25);

                background-color:       #323232;
                    
                z-index:                1;

	}

	#controls {
		position:	absolute;

                top:                    0;
                
                padding:                0;
                margin:                 0;

                width:                  100%;
                min-height:             9rem;
                max-height:             100%;

                background:             #7D7D7D;
	}

</style>








