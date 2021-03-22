<script>
	import { bind, each } from "svelte/internal";

	// Import componenten van andere files met deze syntax, Geef de componenten altijd aan met een Hoofdletter
	import Navbar from "./Navbar.svelte";
	import Player from "./Player.svelte";
	import AddPlayer from "./AddPlayer.svelte";

	let players = [
		{
			name: "Daniël Cool",
			points: 56,
		},
		{
			name: "Nigel Brown",
			points: 109,
		},
		{
			name: "Debbie Harry",
			points: 142,
		},
	];

	const addPlayer = e => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	};

	// Met filter kan je makkelijk elementen zoeken in een array en deze dan wissen.
	// messages = messages.filter(m => m !== 'hello');
	const deletePlayer = (e) => {
		const deletedPlayerName = e.detail;
		players = players.filter(player => player.name !== deletedPlayerName);
	};
</script>

<main>
	<!-- Zo simpel is het om een component in svelte aan te roepen in html markup -->
	<Navbar />
	<div class="container">
		<AddPlayer on:addplayer={addPlayer}/>
		{#if players.length === 0}
			<p class="text-center">No Players</p>
		{:else}
			{#each players as player}
				<Player name={player.name} points={player.points} on:deleteplayer={deletePlayer}/>
			{/each}
		{/if}
	</div>
</main>
