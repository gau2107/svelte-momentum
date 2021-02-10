<script>
    export let quote;
</script>
{#if quote}
    <h1>{quote.quote} - {quote.author}</h1>
{/if}