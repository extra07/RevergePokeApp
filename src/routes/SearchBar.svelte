<script lang="ts">
  import PokemonApi from "./PokemonApi.svelte";

  let searchTerm = $state('');

  $effect(() => {
    // TO DO: implement search logic here
    console.log(`Searching for: ${searchTerm}`);
  });
</script>

<input
  type="search"
  bind:value={searchTerm}
  placeholder="Search..."
/>

<PokemonApi bind:theSearchTerm={searchTerm} />

<style>
  input[type="search"] {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
</style>