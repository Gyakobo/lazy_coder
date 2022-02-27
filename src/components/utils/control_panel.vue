<template>
	<div class="control_panel">
		<div id="left_side">
			<div class="Description">
				<div id="child_Description_banner">
					<p>Description</p>	
				</div>
				
				<div id="child_Description_text">
					<!--<p>Welcome to Lazy_Coder</p>-->	
				</div>
			</div>

			<GPIO_controls/>
		</div>
		
	
		<div id="right_side"></div>
	</div>

</template>


<script>
import GPIO_controls from "./GPIO_controls.vue";

export default {
	components: {
		GPIO_controls,
	},

	mounted() {
		this.emitter.on("Test_Emitter", (msg) => {
			console.log(msg);
		});
	},
};
	
</script>



<style>
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







