<template>
	<div class="control_panel_gpio">
		<div id="banner">
			<p>{{ Name }} pin</p>
		</div>
		
		<div id="controls">


			<div id = "panel">
				<p id=parName>GPIO</p>

				<div id="redDiv"  v-if="Gpio_type==0"></div>
				<div id="blueDiv" v-if="Gpio_type==1"></div>
				
				<div class="dropdown">
					<button class="dropbtn">Setup</button>	
					<div class="dropdown-content">
						<a @click="Gpio_type=0" v-if="Gpio_type==1">OUTPUT</a>
						<a @click="Gpio_type=1" v-if="Gpio_type==0">INPUT</a>
					</div>
				</div>
			</div>

			<modes_vue
				v-for = "(item, index) in modes[Gpio_type]"
				:key = "index"

				:Mode = "nomenclature[Gpio_type][index]"
				:DropDown = "modes[Gpio_type][index]"
			/>
		</div>
	</div>

</template>



<script>
import modes_vue from "./modes_vue.vue";

let set = [
        {
                "Speed":                ["OUTPUT_50MHz", "OUTPUT_2MHz", "OUTPUT_10MHz"],
                "Mode_Specific":        ["output_GP_pushpull", "output_GP_opendrain", "output_AF_pushpull", "output_AF_opendrain"]
        },
        {
                "Mode_Specific":        ["input_analog_mode", "input_floating_input", "input_with_pullupdown"]
        }
];

let preset = [
	{ "Speed":"SPEED", "Mode_Specific":"MODE"}, 
	{ "Mode_Specific":"MODE"} 
];


export default {
	data() {
		return {
			Gpio_type:	0,
			modes:		set,		
			nomenclature:	preset,
		}
	}, 

	components: {
		modes_vue,
	},

	props: {
		Name: String,
	},

	methods: {
		edit_file(msg) {
			this.emitter.emit("Edit_File", msg);
		},
	}
}

</script>



<style>
	#redDiv {
		position:	absolute;

		top:		0.59rem;
		left:		19%;

		width:		0.8rem;
		height:		0.8rem;

		background:	red;	

		border-radius:	50%;
	}

	#blueDiv {
		position:	absolute;

		top:		0.59rem;
		left:		19%;

		width:		0.8rem;
		height:		0.8rem;

		background:	blue;	

		border-radius:	50%;
	}

	


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








