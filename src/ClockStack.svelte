<script>
  import Clock from "./Clock.svelte";
  import Stopwatch from "./Stopwatch.svelte";
  import Pomodoro from "./Pomodoro.svelte";
  import Timer from "./Timer.svelte";
  $: active = "Clock";
  function changeStatus(arg) {
    active = arg;
  }
</script>

{#if active === "Clock"}
  <Clock />
{/if}
{#if active === "Pomodoro"}
  <Pomodoro />
{/if}
{#if active === "Timer"}
  <Timer />
{/if}
{#if active === "Stopwatch"}
  <Stopwatch />
{/if}

<div class="textCenter">
  <img
    class="clockIcons"
    tooltip="Clock"
    on:click={() => changeStatus("Clock")}
    src="/assets/png/clock.png"
    alt="Clock"
  />
  <img
    class="clockIcons"
    tooltip="Pomodoro"
    on:click={() => changeStatus("Pomodoro")}
    src="/assets/png/pomodoro.png"
    alt="Pomodoro"
  />
  <img
    class="clockIcons"
    tooltip="Timer"
    on:click={() => changeStatus("Timer")}
    src="/assets/png/timer.png"
    alt="Timer"
  />
  <img
    class="clockIcons"
    tooltip="Stopwatch"
    on:click={() => changeStatus("Stopwatch")}
    src="/assets/png/stopwatch.png"
    alt="Stopwatch"
  />
</div>
