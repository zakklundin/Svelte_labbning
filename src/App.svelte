<script>
import { insert } from "svelte/internal";


	export let inputNumber = 0;
	let resultNumber = 0
	let selected = 'Choose below'
	let selected2 = 'Choose below'

	function insertButton(div, name, text, multiplier){
		name = document.createElement("button")
		name.innerHTML = text
		name.onclick = function(){
			resultNumber = inputNumber * multiplier
			selected2 = name
		}
		div.appendChild(name)
	}

	function fromCubM(){
		cubicM = true
		squareM = false
		litre = false
		selected = 'Cubic meter(s)'
		let toUnit = document.getElementById("toUnit")
		toUnit.innerHTML = ""
		let btn1 = "toCubicCM"
		let btn2 = "toLitre"
		let btn3 = "toCubicMM"
		insertButton(toUnit, btn1, "Cubic Centimeters", 1000000)
		insertButton(toUnit, btn2, "Litres", 1000)
		insertButton(toUnit, btn3, "Cubic Millimeters", 1000000000)
	}
	function fromSqM(){
		squareM = true
		cubicM = false
		litre = false
		selected = 'Square meter(s)'
		let toUnit = document.getElementById("toUnit")
		toUnit.innerHTML = ""
		let btn1 = "toSqCM"
		let btn2 = "toHA"
		insertButton(toUnit, btn1, "Square Centimeters", 10000)
		insertButton(toUnit, btn2, "Hectares", 0.0001)
	}
	function fromLitre(){
		litre = true
		squareM = false
		cubicM = false
		selected = 'Litre(s)'
		let toUnit = document.getElementById("toUnit")
		toUnit.innerHTML = ""
		let btn1 = "toCubicCM"
		let btn2 = "toLitre"
		let btn3 = "toCubicMM"
		insertButton(toUnit, btn1, "Cubic Centimeters", 1000)
		insertButton(toUnit, btn2, "Litres", 1)
		insertButton(toUnit, btn3, "Cubic Millimeters", 1000000)
	}
/*
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
			resultNumber = inputNumber * 1000
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
*/
</script>

<main>
	<h1>Unit Converter and Calculator</h1>

	<input type="number" bind:value={inputNumber}>

	<p>From: {selected}</p>
	<button id="SqM" on:click={fromSqM}>Square Meters</button>
	<button id="CubeM" on:click={fromCubM}>Cubic Meters</button>
	<button id="Litre" on:click={fromLitre}>Litres</button>
	
	<p>To: {selected2}</p>

	<div id="toUnit">

	</div>
	
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