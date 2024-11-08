<script lang="ts">

    let {pokemonData} = $props();
    let theFoundPokemon = $derived( JSON.parse(JSON.stringify(pokemonData)));
</script>

{#if theFoundPokemon}
    <img src = {theFoundPokemon.sprites.other.showdown.front_default} alt="pokemon" />

    <table>
        <thead>
            <tr>
            <th>Category</th>
            <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
            <td>Abilities</td>
            <td>
            {#each theFoundPokemon.abilities as ability}
                <span class="highlight c1">{ability.ability.name}</span>
            {/each}
            </td>
            </tr>
            <tr>
                <td>Types</td>
                <td>
                {#each theFoundPokemon.types as type}
                    <span class="highlight c2">{type.type.name}</span>
                {/each}
                </td>
            </tr>
            <tr>
            <td>Moves</td>
            <td>
            {#each theFoundPokemon.moves as move}
                <span class="highlight c3">{move.move.name}</span>
            {/each}
            </td>
            </tr>
        </tbody>
    </table>
{/if}

<style>
    table {
        border-collapse: collapse;
        width: 100%;
        margin-bottom: 20px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    th, td {
        padding: 15px;
        text-align: left;
        border-bottom: 1px solid #ddd;
    }

    th {
        background-color: #f0f0f0;
        color: #333;
        font-weight: bold;
    }

    td {
        background-color: #fff;
        color: #666;
        line-height: 1.5em;
    }

    th:first-child, td:first-child {
        padding-left: 20px;
    }

    th:last-child, td:last-child {
        padding-right: 20px;
    }

    tbody tr:hover {
        background-color: #f9f9f9;
    }

    .highlight {
        font-family: -apple-system,BlinkMacSystemFont,Segoe UI,roboto,Helvetica Neue,helvetica,arial,sans-serif;
        color: #fff;
        padding: 3px 8px;
        border-radius: 4px;
        font-weight: 500;
        font-size: small;
        margin: auto 1px;
        box-shadow: 1px 1px #dbdbdb;
    }
    .c1 {
        background-color: #e65100;
    }
    .c2 {
        background-color: #4CAF50;
    }
    .c3 {
        background-color: #2196F3;
    }
</style>