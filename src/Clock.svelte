<script>
  let curTime = incrementTime();
  setInterval(() => {
    curTime = incrementTime();
  }, 1000);

  function incrementTime() {
    let cur = new Date();
    let h = cur.getHours().toString();
    h = h.length === 1 ? "0" + h : h;
    let m = cur.getMinutes().toString();
    m = m.length === 1 ? "0" + m : m;
    return h + ":" + m;
  }
</script>

{#if curTime}
  <h1 class="clock">{curTime}</h1>
{/if}
