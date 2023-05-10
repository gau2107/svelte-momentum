<script>
  import ClockStack from "./ClockStack.svelte";
  import Greeting from "./Greeting.svelte";
  import MainFoucs from "./MainFoucs.svelte";
  import Quote from "./Quote.svelte";
  import Todos from "./Todos.svelte";
  import Weather from "./Weather.svelte";

  let scape = window.window.innerWidth > 768 ? "landscape" : "potrait";
</script>

<body
  class="noSelect main"
  style={`background-image: url('https://source.unsplash.com/daily?${scape}')`}
>
  <Quote />
  <Weather />
  <ClockStack />
  <Greeting />
  <MainFoucs />
  <Todos />
</body>
