<script lang="ts">
    import { fade, fly } from 'svelte/transition';
    import { storeDrawer } from "./store";

    function drawerClose(): void {
        storeDrawer.set(false);
    }
</script>

{#if $storeDrawer === true}

    <!-- Drawer -->
    <div id="drawer" transition:fly|local={{ x: -280, y: 0, duration: 200 }}>
        (drawer contents)
    </div>

    <!-- Backdrop -->
    <!--
        NOTE:
        Try switching between the two lines below to reproduce the issue
        When a second transition is present the fly animation breaks!
    -->
    <div id="backdrop" on:click={()=>{drawerClose()}}></div>
    <!-- <div id="backdrop" on:click={()=>{drawerClose()}} transition:fade|local={{ duration: 200 }}></div> -->

{/if}

<style>
    #drawer {
        background: #242424; padding: 20px; width: 280px;
        position: fixed; top: 0; left: 0; bottom: 0; z-index: 999;
    }
    #backdrop {
        background: rgba(0,0,0,0.5);
        position: fixed; top: 0; left: 0; right: 0; bottom: 0; z-index: 888;
    }
</style>