<script lang="ts">

    let {searchTerm = $bindable('')} = $props();
</script>

<input
    type="search"
    bind:value={searchTerm}
    placeholder="Search..."
/>

<style>
    input[type="search"] {
        width: 100%;
        padding: 10px;
        font-size: 16px;
        border: 1px solid #ccc;
        border-radius: 4px;
    }
</style>