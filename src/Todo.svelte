<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let current;
    export let index;
    function clear() {
        dispatch('deleteTodo', index);
    }
    function checked() {
        dispatch('checkTodo', index);
    }
</script>

<div>
    {#if current.checked}
    <img class="delete" src="/assets/svg/thumb-up.svg" alt="Checked">
    {:else}
    <input class="checkmark" type="checkbox" bind:checked={current.checked} on:click={checked}>
    {/if}
    <span class={current.checked ? "checked mainFocus" : "mainFocus"}>{current.title}</span>
    <img on:click={clear} class="delete" src="/assets/svg/delete.svg" alt="Delte">
</div>