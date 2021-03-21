<script>
	let name = 'Daniël';
	let beltColour = 'black';

	function handleClick() {
		beltColour = 'white';
	};

	function handleInput(e) {
		beltColour = e.target.value;
	}
</script>

<main>
	<!-- Door een variable in {curly braces} te zetten zorg je ervoor dat je inline aan html javascript code toe kan voegen -->
	<h1>Hello {name}!</h1>
	<p style = "color: {beltColour}">{beltColour} belt.</p>

	<!-- met de on:click functie geef je aan wat de knop moet uitvoeren wanneer deze geklikt is -->
	<button on:click = {handleClick}>update belt colour</button>

	<!-- Op deze manier bind je data met andere data, dit noem je eenzijdige data-binding want de verandering gaat maar één-wegs -->
	<!--<input type="text" on:input="{handleInput}">-->

	<!-- Op deze manier bind je data tweezijdig, beide uiteindes veranderen elkaars staat wanneer haar eigen staat verandert -->
	<!--<input type="text" on:input="{handleInput}" value ={beltColour}>-->

	<!-- Er is ook een manier om tweezijdige binding af te korten namelijk: -->
	<input type="text" bind:value = {beltColour}>

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