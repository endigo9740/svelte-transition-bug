<script lang="ts">
    import Drawer from "$lib/Drawer.svelte";
    import { storeDrawer } from "$lib/store";

    function drawerOpen(): void {
        storeDrawer.set(true);
    }
</script>

<Drawer />

<main>
    <h1>Homepage</h1>
    <p>Tap the button below to open the drawer component.</p>
    <button on:click={()=>{drawerOpen()}}>Open Drawer</button>

    <hr>

    <h2>Store State</h2>
    <pre>$storeDrawer: {$storeDrawer}</pre>
</main>