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

    function edit() {
        dispatch('setEditForm', index)
    }
</script>

<div>
    {#if current.checked}
    <img class="delete" src="/assets/svg/thumb-up.svg" alt="Checked">
    {:else}
    <input class="checkMark" type="checkbox" bind:checked={current.checked} on:click={checked}>
    {/if}
    <span on:click={edit} class={current.checked ? "checked mainFocus" : "mainFocus"}>{current.title}</span>
    <img on:click={clear} class="delete" src="/assets/svg/delete.svg" alt="Delte">
</div>