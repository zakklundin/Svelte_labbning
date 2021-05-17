<script>
	export let inputNumber = 0;
	let resultNumber = 0
	let cubicM = false
	let squareM = false
	let litre = false
	let selected = 'Choose below'
	let selected2 = 'Choose below'

	function fromCubM(){
		cubicM = true
		squareM = false
		litre = false
		selected = 'Cubic meter(s)'
	}
	function fromSqM(){
		squareM = true
		cubicM = false
		litre = false
		selected = 'Square meter(s)'
	}
	function fromLitre(){
		litre = true
		squareM = false
		cubicM = false
		selected = 'Litre(s)'
	}

	function toSqCM(){
		if (cubicM == true || litre == true) {
			resultNumber = "ERROR, incompatible units"
		} else if (squareM == true){
			resultNumber = inputNumber * 1000
		}
		selected2 = 'Square Centimeter(s)'
	}

	function toCubCM(){
		if (squareM == true){
			resultNumber = "ERROR, incompatible units"
		} else if (cubicM == true) {
			resultNumber = inputNumber * 1000000
		} else if (litre == true) {
			resultNumber = inputNumber * 1000
		}
		selected2 = 'Cubic Centimeter(s)'
	}
	function toLitre() {
		if (squareM == true){
			resultNumber = "ERROR, incompatible units"
		} else if (cubicM == true) {
			resultNumber = inputNumber * 0.001
		} else if (litre == true) {
			resultNumber = inputNumber
		}
		selected2 = 'Litre(s)'
	}
	function toHA(){
		if (cubicM == true || litre == true){
			resultNumber = "ERROR, incompatible units"
		} else if (squareM == true) {
			resultNumber = 10000 * inputNumber
		}
		selected2 = 'Hectare'
	}
	function toCubMM(){
		if (squareM == true){
			resultNumber = "ERROR, incompatible units"
		} else if (cubicM == true){
			resultNumber = inputNumber * 1000000000
		} else if (litre == true){
			resultNumber = inputNumber * 1000000
		}
		selected2 = "Cubic Millimeter(s)"
	}

</script>

<main>
	<h1>Unit Converter and Calculator</h1>

	<input type="number" bind:value={inputNumber}>

	<p>From: {selected}</p>
	<button id="SqM" on:click={fromSqM}>Square Meters</button>
	<button id="CubeM" on:click={fromCubM}>Cubic Meters</button>
	<button id="Litre" on:click={fromLitre}>Litres</button>
	
	<p>To: {selected2}</p>
	<button id="SqCM" on:click={toSqCM}>Square Centimeters</button>
	<button on:click={toHA}>Hectare</button>
	<button id="CubeCM" on:click={toCubCM}>Cubic Centimeters</button>
	<button on:click={toLitre}>Litres</button>
	<button on:click={toCubMM}>Cubic Millimeter</button>

	<p>Result: {resultNumber}</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>