<script>
  let timer = 1500; // 25 minutes in seconds
  let targetTime;
  let displayTime = setDisplayTime();

  const pomodoro = setInterval(() => {
    let currentTime = +new Date(); // Get the current timestamp
    displayTime = setDisplayTime();
    if (currentTime >= targetTime) {
      playSound();
      clearInterval(pomodoro);
    }
    if (editMode) clearInterval(pomodoro);
  }, 1000);

  function setDisplayTime() {
    timer -= 1;
    targetTime = +new Date() + timer * 1000;
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
