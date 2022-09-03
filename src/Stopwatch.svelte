<script>
  let elapsedTime = 0;
  let displayTime = 0;
  setInterval(() => {
    elapsedTime += 1;
    let fM = elapsedTime / 100; //fM in seconds
    let m = parseInt(fM / 60);
    let s = m === 0 ? parseInt(fM) : parseInt(fM % 60);
    let ms = elapsedTime % 100;
    displayTime =
      (m < 10 ? "0" + m : m) +
      ":" +
      (s < 10 ? "0" + s : s) +
      ":" +
      (ms < 10 ? "0" + ms : ms);
  }, 10);
</script>

{#if displayTime}
  <h1 class="clock">{displayTime}</h1>
{/if}
