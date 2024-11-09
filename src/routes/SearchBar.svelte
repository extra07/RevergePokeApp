<script lang="ts">
    import {suggestions} from './pokemons.svelte.js';
    let {searchTerm = $bindable<string>('')} = $props();
    let showList = $state(false);
    let filteredSuggestions: { name: string; url: string; }[] = $state([]);

    $effect(() => {
        filteredSuggestions = suggestions.results
                            .filter(result => result.name.toLowerCase()
                            .includes((searchTerm as string)
                            .toLowerCase()))
                            .slice(0, 10);
    });
</script>

<input
    type="search"
    bind:value={searchTerm}
    placeholder="Search..."
    oninput={() => {showList = true}}
/>
<div class="pos-rel">
{#if showList}
<ul>
    {#each filteredSuggestions as suggestion}
        <li>
        <a href="#top" onclick={() => {
            searchTerm = suggestion.name;
            showList = false;
        }}>{suggestion.name}</a>
        </li>
    {/each}
</ul>
{/if}
</div>
<style>
    input[type="search"] {
        width: 100%;
        padding: 10px;
        font-size: 16px;
        border: 1px solid #ccc;
        border-radius: 4px;
    }
    .pos-rel {
        position: relative;
        width: 100%;
    }
    ul {
        position: absolute;
        top: 0;
        left: 0;
        list-style-type: none;
        padding: 1px;
        margin: 0;
        background-color: #c7c2c2;
    }

    li {
        margin-bottom: 1px;
    }

    a {
        display: block;
        padding: 10px;
        background-color: #f5f5f5;
        color: #333;
        text-decoration: none;
        border-radius: 5px;
        transition: background-color 0.3s ease;
    }

    a:hover {
        background-color: #e5e5e5;
    }
</style>