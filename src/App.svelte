<script>
	import ClockStack from "./ClockStack.svelte";
	import Greeting from "./Greeting.svelte";
	import MainFoucs from "./MainFoucs.svelte";
	import Quote from "./Quote.svelte";
	import Todos from "./Todos.svelte";
	import Weather from "./Weather.svelte";

	// let image = null;
	// getBackgroundImage();

	// async function getBackgroundImage () {
	// 	const res = await fetch('https://picsum.photos/1280/720.webp', {
	// 		method: 'GET'
	// 	})
	// 	image = await res.url;
	// }
</script>

<!-- {#if image} -->
	<body class="noSelect" style="background-image: url('https://source.unsplash.com/daily?landscape')">
		<Quote />
		<Weather />
		<ClockStack/>
		<Greeting />
		<MainFoucs />
		<Todos />
	</body>
<!-- {/if} -->
