<script>
import Quote from "./Quote.svelte";

	// TODO move into seperate components
	let image = null;
	getBackgroundImage();
	async function getBackgroundImage () {
		const res = await fetch('https://picsum.photos/1280/720.webp', {
			method: 'GET'
		})
		image = await res.url;
	}
</script>
<!-- BUG remove upper white space -->
{#if image}
<body style="background-image: url('{image}')">
	<Quote />
</body>
{/if}