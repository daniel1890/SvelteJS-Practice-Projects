<script>
import { bind } from "svelte/internal";
// Import componenten van andere files met deze syntax, Geef de componenten altijd aan met een Hoofdletter
import Navbar from "./navbar.svelte";

	let name = 'Daniël Cool';
	let points = 100;
	let showControls = false;

	function addPoint() {
		points += 1;
	}

	// zelfde type functie kan ook op deze manier geschreven worden met arrow functie
	const removePoint = () => (points -= 1);

	// met de ^= operator toggle je tussen een boolean, kan ook als (showControls = !showControls)
	const toggleControls = () => (showControls ^= true);
</script>

<main>
	<!-- Zo simpel is het om een component in svelte aan te roepen in html markup -->
	<Navbar/>
	<div class ="container">
		<div class="card">
			<h1>
				{name}
				<button class="btn btn-sm" on:click={toggleControls}>
					{#if showControls} - {:else}+{/if}
				</button>
			</h1>
			<h3>Points: {points}</h3>
			{#if showControls}
				<button class="btn" on:click={addPoint}>+1</button>
				<button class="btn btn-dark" on:click={removePoint}>-1</button>
				<input type="number" bind:value={points} />
			{/if}			
		</div>
	</div>
</main>

<style>
	main {
		text-align: justify;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #204f6e;
	}

	h3 {
		margin-bottom: 10px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>