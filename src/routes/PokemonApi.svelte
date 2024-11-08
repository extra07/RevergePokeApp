<script lang="ts">

    let data = $state(null);
    let {theSearchTerm = $bindable(''), theFoundPokemon = $bindable({})} = $props();

    $effect(() => {
        console.log(data);
    });

    $effect(() => {
        search(theSearchTerm);
    });

    async function search(pokemon: unknown) {
    try {
        const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${theSearchTerm}`);
            const jsonData = await response.json();
            data = jsonData;
            theFoundPokemon = data;
        } catch (error) {
            // console.error(error);
        }
    }
</script>

