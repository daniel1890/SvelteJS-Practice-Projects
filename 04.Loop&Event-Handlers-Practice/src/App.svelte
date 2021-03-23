<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let people = [
    { name: "yoshi", beltColour: "green", age: 25, id: 1 },
    { name: "mario", beltColour: "black", age: 50, id: 2 },
    { name: "bowser", beltColour: "yellow", age: 100, id: 3 },
  ];

  const handleClick = (id) => {
    people = people.filter((p) => p.id !== id);
  };
</script>

<main>
  {#each people as p (p.id)}
    <div>
      <h4>{p.name}</h4>
      <p>{p.age} years old, {p.beltColour} belt.</p>
      <!-- met deze syntax {() => } geef je aan, wanneer de listener iets hoort voer dit uit: ....
	    	in dit geval is het de handleClick functie die p.id als parameter meeneemt.
      De volledige functie kan ook inline geschreven worden, dan heet het een inline functie alleen wordt de code dan moeilijk leesbaar. -->
      <button on:click={() => handleClick(p.id)}>delete</button>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
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
