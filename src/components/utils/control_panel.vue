<template>
	<div class="control_panel">
		<div id="left_side">
			<div class="Description">
				<div id="child_Description_banner">
					<p >Generated Code</p>	
				</div>
				
				<div id="child_Description_text">
					<Board_vue id = "board-1">
						<Card_vue id="card-1" draggable="true">
							<p>Card one</p>			
						</Card_vue>	
					</Board_vue>
				
				</div>
			</div>

			<GPIO_controls
				v-for = "(item, index) in pins"
				:key = "index"

				:Name = "item"
			/>
		</div>
		
	
		<div id="right_side">
			<Board_vue id = "board-2">
				<Card_vue id="card-2" draggable="true">
					<p>Card two</p>			
				</Card_vue>	
			</Board_vue>
		</div>
	</div>

</template>


<script>
import GPIO_controls from "./GPIO_controls.vue";
import Board_vue from "./Board_vue.vue";
//import Card_vue from "./Card_vue.vue";


export default {
	//mixins: [STM32F1BoardMixin],

	data() {
		return {
			pins: [],
			board: this.$refs.code,
		}
	},


	components: {
		GPIO_controls,
		Board_vue,
		//Card_vue,
	},

	mounted() {
		this.emitter.on("Test_Emitter", (msg) => {
			//console.log(this.pins);

			

			if (!this.pins.includes(msg)) {
				this.pins.push(msg);
			}
			
			else {
				const index = this.pins.indexOf(msg);
				if (index > -1) {
					this.pins.splice(index, 1); 
				}
			}
				
		});

		/*this.emitter.on("Edit_File", (msg) => {
			if (msg == "outputConfig_on") {	
				file[] = msg;	
			}
		});*/ 	
	},
};
	
</script>



<style>
	#card-1 {
		position:	relative;
		background:	gray;

		width:		8rem;
		height:		2rem;
		font-family: 'Roboto', sans-serif;
		font-style: normal;
		font-weight: 490;
		font-size: 17px;
		line-height: 28px;
		text-align: center;

		color: #FFFFFF;
	}
	#card-2 {
		position:	relative;
		background:	gray;
		
		width:		8rem;
		height:		2rem;
		font-family: 'Roboto', sans-serif;
		font-style: normal;
		font-weight: 490;
		font-size: 17px;
		line-height: 28px;
		text-align: center;

		color: #FFFFFF;
	}




	#board-1 {
		position:	absolute;

		width:		100%;
		height:		100%;

		border:		1px solid red;
	}
	#board-2 {
		position:	absolute;

		width:		100%;
		height:		100%;

		border:		1px solid red;
	}




	p {
		@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

		position:		absolute;
		
		padding:		0;
		margin:			0;

		top:			9%;
		left:			40px;
		
		font-family: 'Roboto', sans-serif;
		font-style: normal;
		font-weight: 490;
		font-size: 17px;
		line-height: 28px;
		text-align: center;

		color: #FFFFFF;
	}

	.Description {
		position:		relative;

		top:			0;

		padding:		0;
		margin:			0;
	
		width:			100%;
		max-height:		16rem;

		/*border-bottom:		1px solid gray;

		margin-bottom:		5px;*/
	}	
	
	#child_Description_banner {	
		position:		relative;
		
		top:			0;
		
		padding:		0;
		margin:			0;
		
		width:			100%;
		height:			30px;

		box-shadow:		0px 9px 15px rgba(0, 0, 0, 0.25);

		background-color:	#323232;
		
		z-index:		1;
	}
	#child_Description_text {	
		position:		relative;

		top:			0;
		
		padding:		0;
		margin:			0;

		width:			100%;
		min-height:		9rem;
		max-height:		100%;

		background:		#797d64;

	}






	.control_panel {
		position:		absolute;

		width:			50vw;
		height:			100vh;

		right:			0;
		top:			0;

		margin:			0;
		padding:		0;

		background-color:	#575757;

		border:			3px solid gray;
	}

	#left_side {
		position:		absolute;
	
		left:			0;
		top:			0;

		padding:		0;
		margin:			0;

		width:			50%;
		height:			100%;

		border-right:		3px solid gray;
	}

	#right_side {
		position:		absolute;

		right:			0;
		top:			0;
		
		padding:		0;
		margin:			0;

		width:			50%;
		height:			100%;

		border-left:		3px solid gray;
		
		background-color:	white;
	}

</style>







