<script>
import { insert } from "svelte/internal";


	export let inputNumber = 0;
	let resultNumber = 0
	let selected = 'Choose below'
	let selected2 = 'Choose below'

	function insertButton(div, btn, text, multiplier){
		btn = document.createElement("button")
		btn.innerHTML = text

		btn.style.backgroundColor= "#f44336"
  		btn.style.border = "none"
  		btn.style.color = "white"
  		btn.style.padding = "15px 32px"
  		btn.style.alignContent = "center"
  		btn.style.textDecoration = "none"
  		btn.style.display= "inline-block"
  		btn.style.fontSize = "16 px"

		btn.onclick = function(){
			resultNumber = inputNumber * multiplier
			selected2 = text
		}
		div.appendChild(btn)
	}

	function fromCubM(){
		selected = 'Cubic meters'
		let toUnit = document.getElementById("toUnit")
		toUnit.innerHTML = ""
		let btn1 = "toCubicCM"
		let btn2 = "toLitre"
		let btn3 = "toCubicMM"
		let btn4 = "tomLitre"
		insertButton(toUnit, btn1, "Cubic Centimeters", 1000000)
		insertButton(toUnit, btn2, "Litres", 1000)
		insertButton(toUnit, btn3, "Cubic Millimeters", 1000000000)
		insertButton(toUnit, btn4, "Millilitres", 1000000)
	}
	function fromSqM(){
		selected = 'Square meters'
		let toUnit = document.getElementById("toUnit")
		toUnit.innerHTML = ""
		let btn1 = "toSqCM"
		let btn2 = "toHA"
		let btn3 = "toSqF"
		insertButton(toUnit, btn1, "Square Centimeters", 10000)
		insertButton(toUnit, btn2, "Hectares", 0.0001)
		insertButton(toUnit, btn3, "Square Feet", 0.00107639104)
	}
	function fromLitre(){
		selected = 'Litres'
		let toUnit = document.getElementById("toUnit")
		toUnit.innerHTML = ""
		let btn1 = "toCubicCM"
		let btn2 = "toCubicM"
		let btn3 = "toCubicMM"
		insertButton(toUnit, btn1, "Cubic Centimeters", 1000)
		insertButton(toUnit, btn2, "Cubic Meters", 0.001)
		insertButton(toUnit, btn3, "Cubic Millimeters", 1000000)
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

	<div id="toUnit"></div>

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

	button {
  		background-color: #f44336;
  		border: none;
  		color: white;
  		padding: 15px 32px;
  		text-align: center;
  		text-decoration: none;
  		display: inline-block;
  		font-size: 16px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>