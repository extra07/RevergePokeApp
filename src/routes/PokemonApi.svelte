<script lang="ts">

    let {theSearchTerm = $bindable(''), theFoundPokemon = $bindable({})} = $props();

    $effect(() => {
        search(theSearchTerm);
    });

    async function search(pokemon: unknown) {
    try {
        const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`);
            const jsonData = await response.json();
            theFoundPokemon = jsonData;
        } catch (error) {
            // console.error(error);
        }
    }
</script>

