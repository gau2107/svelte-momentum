<script>
	import Clock from "./Clock.svelte";
import Quote from "./Quote.svelte";
	import Weather from "./Weather.svelte";
	let quote = null;
	getBackgroundImage();

	async function getBackgroundImage() {
		const res = await fetch("https://quotes.rest/qod?language=en", {
			method: "GET",
			accept: "application/json",
		});
		let resInJson = await res.json();
		quote = resInJson.contents.quotes[0];
	}
</script>

<!-- BUG remove upper white space -->
{#if quote}
	<body style="background-image: url('{quote.background}')">
		<Quote {quote} />
		<Weather />
		<Clock />
	</body>
{/if}
