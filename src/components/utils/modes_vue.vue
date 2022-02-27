<template>
	<div id="panel">
		<p id=parName>{{ Mode }}</p>

		<div class="dropdown">
			<button class="dropbtn">Setup</button>                            
			<div class="dropdown-content">
				<a 	v-for = "(item, index) in DropDown"
					:key = "index"	
				>
					{{ item }}	
				</a>

			</div>
		</div>
	</div>
</template>


<script>
export default {
	data() {
		return {
		}
	},

	props:	{
		Mode:		String,
		DropDown:	Array,
	},
};

</script>


<style>
	#parName {
		position:	absolute;

		left:		4px;	
	}

	#panel {
		position: 	relative; 
		
		top:		42px;

		height:		1.8rem;
		width:		100%;

		padding:	0;
		margin:		0;

		/*border:		1px solid white;*/

		cursor: pointer;
		margin-bottom:	5px;	
	}

	.dropbtn {
		position:       relative;

		top:		3px;
		right:		26%;

		margin:         0;
		padding: 	0;
	
		height:		1.4rem;
		width:		13rem;

		background-color: #7a7a7a;
		color: white;
        
		font-size: 16px;
		border: none;

		border-radius:  1px;
                
		box-shadow: 0px 0px 14px rgba(0,0,0,0.4);
	}               
        .dropdown {
                position: absolute;
                display: inline-block;
        }

        .dropdown-content {
                display: none;
                position: absolute;
                background-color: #f9f9f9;
                min-width: 160px;
                box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
                z-index: 2;
        }

        .dropdown-content a {
                color: black;
                padding: 8px 8px;
                text-decoration: none;
                display: block;
        }

        .dropdown-content a:hover {background-color: #cfcfcf}

        .dropdown:hover .dropdown-content {
                display: block;
        }

        .dropdown:hover .dropbtn {
                background-color: #3e8e41;
        }

</style>


