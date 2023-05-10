<script>
  let quote = null;
  getQuote();
  async function getQuote() {
    const res = await fetch("https://api.quotable.io/random", {
      method: "GET",
      accept: "application/json",
    });
    let resInJson = await res.json();
    quote = resInJson;
  }
</script>

{#if quote}
  <span class="quote">{quote.content} - {quote.author}</span>
{/if}
