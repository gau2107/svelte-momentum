<script>
	// TODO move into seperate components
	let image = null;
	let quote = null;
	getBackgroundImage();
	getQuote();
	async function getBackgroundImage () {
		const res = await fetch('https://picsum.photos/1280/720.webp', {
			method: 'GET'
		})
		image = await res.url;
	}
	async function getQuote () {
		const res = await fetch('https://quotes.rest/qod?language=en', {
			method: 'GET',
			accept: 'application/json'
		})
		let resInJson = await res.json();
		quote = resInJson.contents.quotes[0];
	}
</script>
<!-- BUG remove upper white space -->
{#if image}
<body style="background-image: url('{image}')">
	<h1>{quote.quote}</h1>
</body>
{/if}