<script>
    let curTime = null;
    setInterval(() => {
      let cur = new Date();
        curTime = cur.getHours().toString() +':'+ cur.getMinutes().toString();
    }, 1000);
</script>
<!-- BUG displays 20:0 instead of 20:00 -->
{#if curTime}
<h1 class="clock">{curTime}</h1>
{/if}