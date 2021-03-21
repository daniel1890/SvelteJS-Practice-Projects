<script>
  import { bind, each } from "svelte/internal";

  // Import componenten van andere files met deze syntax, Geef de componenten altijd aan met een Hoofdletter
  import Navbar from "./navbar.svelte";
  import Player from "./player.svelte";

  let players = [
	  {
		name: "Daniël Cool",
		points: 56
	  },
	  {
		name: "Nigel Brown",
		points: 109
	  },
	  {
		name: "Debbie Harry",
		points: 142
	  }
  ];
</script>

<main>
  <!-- Zo simpel is het om een component in svelte aan te roepen in html markup -->
  <Navbar />
  <div class="container">
    {#if players.length === 0}
		<p>No Players</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} />
		{/each}
	{/if}
  </div>
</main>

