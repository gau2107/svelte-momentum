<script>
  let quote = null;
  getQuote();
  async function getQuote() {
    const res = await fetch("https://quotes.rest/qod?language=en", {
      method: "GET",
      accept: "application/json",
    });
    let resInJson = await res.json();
    quote = resInJson.contents.quotes[0];
  }
</script>

{#if quote}
  <span class="quote">{quote.quote} - {quote.author}</span>
{/if}
