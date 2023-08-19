<svelte:head>
	<title>Calculator</title>
	<meta name="description" content="About this app" />
</svelte:head>

<script>

	import'./cacl.css';
	// import'./calc.js';

	 let output = "";
	 let total = 0;
	 /**
   * @type {string | null}
   */
	 let state = null;

	function resolveState(){
		switch(state) {
			case"add":
			total +=parseFloat(output);
			output ="0";
			break;


			case"subtract":
			total -=parseFloat(output);
			output ="0";
			break;


			case"multiply":
			total *=parseFloat(output);
			output ="0";
			break;


			case"divide":
			total /=parseFloat(output);
			output ="0";
			break;

			default:
				total += parseFloat(output);
				output = "0";
				break;
		}

	}

	/**
   * @param {string} operation
   */
	function Operation(operation) {
		resolveState();
		state = operation;
	}


/**
   * @param {string} value
   */
function Input(value) {
	if(output.toString() == "0" ) {
		output = "";
	}
	output = output + value;
	
}
function equal() {
		resolveState();
		output  = total;
		state = "equal";

	}



// function onOperation(value) {
// 	input +=value;
// }


function Clear() {
 output = "";
}


</script>

<body>


	

<div id="mainbody">
	<div>
		<input type="text" bind:value={output} readonly/>
	</div>
	
		<div class="but">
			<div class="row">
			<button on:click={() => Clear()}>C</button>
		</div>

		<div class="row">
			<button on:click={() => Operation("divide")}>&divide</button>
			<button on:click={() => Operation("multiply")}>&times</button>
			<button on:click={() => Operation("subtract")}>-</button>
			<button on:click={() => Operation("add")}>+</button>
		</div>

		<div class="row">
			<button on:click={() => Input('7')}>7</button>
			<button on:click={() => Input('8')}>8</button>
			<button on:click={() => Input('9')}>9</button>
			
		</div>

		<div class="row">
			<button on:click={() => Input('4')}>4</button>
			<button on:click={() => Input('5')}>5</button>
			<button on:click={() => Input('6')}>6</button>
			
		</div>

		<div class="row">
			<button on:click={() => Input('1')}>1</button>
			<button on:click={() => Input('2')}>2</button>
			<button on:click={() => Input('3')}>3</button>
			
		</div>

		<div class="row">
			<button on:click={() => Input('0')}>0</button>
			<button on:click={() => Input(".")}>.</button>
			<button on:click={equal}>=</button>
			
		</div>


		</div>
	
</div> 
</body>