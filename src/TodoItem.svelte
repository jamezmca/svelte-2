<script>
    import { fade, fly } from "svelte/transition";
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function remove() {
        dispatch("remove", { id });
    }

    function toggleStatus() {
        let newStatus = !complete;
        dispatch("toggle", {
            id,
            newStatus,
        });
    }

    export let id; // document ID
    export let text;
    export let complete;
</script>

<li in:fly={{ x: 900, duration: 500 }}>
    <span class:complete>{text} </span>
    <!-- //class:complete={complete}  but can use shorthand like above if the same-->
    {#if complete}
        <button on:click={toggleStatus}>check</button>
    {:else}
        <button on:click={toggleStatus}>cross</button>
    {/if}
    <button on:click={remove}>cunt</button>
</li>

<style>
    .complete {
        text-decoration: line-through;
        color: green;
    }
</style>
