<script>
  import { bind } from "svelte/internal";

  // Met het export keyword geef je aan dat het component gebruikt gaat worden buiten dit bestand
  // , in de file waar je het component aanroept kan je dus de variabelen waar export voor staat bepalen.
  export let name;
  export let points;
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
