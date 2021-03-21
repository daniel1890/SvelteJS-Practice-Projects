<script>
	let firstName = 'Jimi';
	let lastName = 'Hendrix';
	let beltColour = 'black';

	/* met de $: syntax geef je aan dat het een reactief element is, dwz dat de staat van het element
	afhangt van de staat van andere elementen in dit geval hangt de staat van 'fullName' af van
	'firstName' en 'lastName' 

	de `` tekens geven aan dat het om een template string gaat, een template string geeft je access
	tot placeholders dit zijn de variabelen enclosed in ${}. Normale quotes '' "" geven je hier geen toegang toe. */
	$: fullName = `${firstName} ${lastName}`;
	$: {
		console.log(beltColour);
		console.log(fullName);
	}

	function handleClick() {
		beltColour = 'white';
	};

	function handleInput(e) {
		beltColour = e.target.value;
	};
</script>

<main>
	<p style = "color: {beltColour}">{fullName} - {beltColour} belt.</p>
	<input type="text" bind:value = {firstName}>
	<input type="text" bind:value = {lastName}>
	<input type="text" bind:value = {beltColour}>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>