<script lang="ts">

    let {pokemonData} = $props();
    let theFoundPokemon = $derived( JSON.parse(JSON.stringify(pokemonData)));
</script>

<textarea rows="20" cols="60" readonly>

        {JSON.stringify(theFoundPokemon)}

</textarea>

{#if theFoundPokemon}
    <img src = {theFoundPokemon.sprites.other.showdown.front_default} alt="pokemon" />
{/if}
