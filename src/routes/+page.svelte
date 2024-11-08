<script lang="ts">

    import PokeDisplay from "./PokeDisplay.svelte";
    import SearchBar from "./SearchBar.svelte";
    import PokemonApi from "./PokemonApi.svelte";

    let toFind = $state("pikachu");
    let wasFound = $state(null);
</script>
<svelte:head>
    <title>Reverge PokeGG!</title>
    <link rel="icon" type="image/png" href="/favicon.ico">
</svelte:head>
<h1>Welcome to Reverge PokeGG!</h1>
<div class="search-container">
    <h2>Current Search: {toFind}</h2>
    <SearchBar bind:searchTerm={toFind} />
    <PokeDisplay pokemonData={wasFound} />
</div>

<PokemonApi bind:theSearchTerm={toFind} bind:theFoundPokemon={wasFound} />

<style>
    .search-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: auto 20%;
    }
    h1 {
        text-align: center;
        font-family: 'Helvetica', sans-serif;
        color: #d94575;
    }
    h2 {
        font-family: -apple-system,BlinkMacSystemFont,Segoe UI,roboto,Helvetica Neue,helvetica,arial,sans-serif;
    }
</style>