<script>
  let timer = 1500;
  let displayTime = setDisplayTime();

  const pomodoro = setInterval(() => {
    displayTime = setDisplayTime();
    timer === 0 && playSound();
    timer === 0 && clearInterval(pomodoro);
  }, 1000);

  function setDisplayTime() {
    timer -= 1;
    let m = parseInt(timer / 60);
    let s = timer % 60;
    return (m < 10 ? "0" + m : m) + ":" + (s < 10 ? "0" + s : s);
  }

  function playSound() {
    const audio = new Audio("/assets/audio/notification.mp3");
    audio.play();
  }
</script>

{#if displayTime}
  <h1 class="clock">{displayTime}</h1>
{/if}
