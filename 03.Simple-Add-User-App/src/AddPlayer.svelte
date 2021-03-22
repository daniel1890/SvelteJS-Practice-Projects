<script>
    import { createEventDispatcher } from "svelte";

    // Een event dispatcher wordt geïmporteerd om event mee te verwerken, wanneer een event verwerkt moet worden moet je deze dus altijd importeren.
    const dispatch = createEventDispatcher();

    let player = {
        name: "",
        points: 0
    };

    // Creeër een const met een "e"(Event) als parameter, met behulp van dispatch
    // wat de createEventDispatcher bevat, hiermee verstuur je de player naar een ander element.
    // Buiten dit component.
    const onSubmit = (e) => {
        e.preventDefault();
        dispatch("addplayer", player);
        player = { 
            name: "",
            points: 0
        };
    };
</script>

<!-- Wanneer op submit gedrukt wordt wordt de functie onSubmit gecalled, deze functie accepteert een event
, deze event behoudt ook alle nodige data die verstuurd wordt met het formulier-->
<form on:submit={onSubmit} class="grid-3">
    <input type="text" placeholder="Player Name" bind:value=
    {player.name} />
    <input type="number" placeholder="Player Score" bind:value=
    {player.points} />
    <input type="submit" class="btn btn-primary" value="Add Player"/>
</form>