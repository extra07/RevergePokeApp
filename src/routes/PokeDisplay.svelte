<script lang="ts">
   let { pokemonData } = $props();

</script>

<textarea rows="20" cols="60" readonly>
    {JSON.stringify(pokemonData)}
</textarea>