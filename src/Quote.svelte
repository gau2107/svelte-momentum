<script>
    export let quote;
</script>
{#if quote}
    <span class="quote">{quote.quote} - {quote.author}</span>
{/if}