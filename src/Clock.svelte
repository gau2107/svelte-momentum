<script>
    let curTime = null;
    setInterval(() => {
      let cur = new Date();
      let h = cur.getHours().toString();
      let m = cur.getMinutes().toString();
      m = m.length === 1 ? '0'+m : m;
        curTime = h +':'+ m;
    }, 1000);
</script>
{#if curTime}
<h1 class="clock">{curTime}</h1>
{/if}