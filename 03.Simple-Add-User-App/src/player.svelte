<script>
  import { bind } from "svelte/internal";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Met het export keyword geef je aan dat het component gebruikt gaat worden buiten dit bestand
  // , in de file waar je het component aanroept kan je dus de variabelen waar export voor staat bepalen.
  export let name;
  export let points;
  let showControls = false;

  function addPoint() {
    points += 1;
  }

  // zelfde type functie kan ook op deze manier geschreven worden met arrow functie, dit is vooral handig voor korte compacte functies
  const removePoint = () => (points -= 1);

  // met de ^= operator toggle je tussen een boolean, kan ook als (showControls = !showControls)
  const toggleControls = () => (showControls ^= true);

  // Stuur de naam van de speler mee en roep deze aan in de main App, door daarna de players [] te filteren mbv de naam verwijder je makkelijk een speler
  const onDelete = () => dispatch("deleteplayer", name);
</script>

<main>
    <div class="card">
      <h1>
        {name}
        <button class="btn btn-sm" on:click={toggleControls}>
          {#if showControls} - {:else}+{/if}
        </button>
        <button class="btn btn-danger btn-sm" on:click={onDelete}>
          X
        </button>
      </h1>

      <h3>Points: {points}</h3>
      {#if showControls}
        <button class="btn" on:click={addPoint}>+1</button>
        <button class="btn btn-dark" on:click={removePoint}>-1</button>
        <input type="number" bind:value={points} />
      {/if}
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
