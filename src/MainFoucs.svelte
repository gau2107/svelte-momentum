<script>
    let mainFocusInput = "";
    let mainFocus = localStorage.getItem("mainFocus");
    function onKeyup(e) {
        if(e.key === 'Enter') {
            mainFocus = mainFocusInput;
            localStorage.setItem("mainFocus", mainFocus);
            mainFocusInput = "";
        }
    }

    function clear() {
        mainFocus = "";
        localStorage.removeItem("mainFocus");
    }
</script>

<div class="center">
    {#if !mainFocus}
    <label class="mainFocus" for> What is your main focus for today?</label>
    <input bind:value={mainFocusInput} on:keyup={e => onKeyup(e)}>
    {:else}
    <div>
        <span class="mainFocus">{mainFocus}</span>
        <img on:click={clear} class="delete" src="/assets/svg/delete.svg" alt="Delte">
    </div>
    {/if}
</div>
