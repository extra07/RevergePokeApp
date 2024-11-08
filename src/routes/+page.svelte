<script>
    import PokeDisplay from "./PokeDisplay.svelte";
    import SearchBar from "./SearchBar.svelte";
    import PokemonApi from "./PokemonApi.svelte";
    let toFind = $state("pikachu");
    let wasFound = $state(null);
</script>
<h1>Welcome to Reverge PokeGG!</h1>
<SearchBar bind:searchTerm={toFind} />
<PokemonApi bind:theSearchTerm={toFind} bind:theFoundPokemon={wasFound} />
<PokeDisplay pokemonData={wasFound} />
