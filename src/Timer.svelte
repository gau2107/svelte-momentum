<script>
  let displayTime = "";
  let editMode = true;
  let targetTime;

  let minInput, secInput;

  function timerLogic(timer) {
    const timerInterval = setInterval(() => {
      let currentTime = +new Date(); // Get the current timestamp
      setDisplayTime();
      if (currentTime >= targetTime) {
        clearInterval(timerInterval);
        !editMode && playSound();
      }
      if (editMode) clearInterval(timerInterval);
    }, 1000);
  }

  function setDisplayTime() {
    let currentTime = +new Date(); // Get the current timestamp
    let timeRemaining = targetTime - currentTime; // Calculate the remaining time in milliseconds
    let secondsRemaining = Math.ceil(timeRemaining / 1000);
    let m = parseInt(secondsRemaining / 60);
    let s = secondsRemaining % 60;
    displayTime = (m < 10 ? "0" + m : m) + ":" + (s < 10 ? "0" + s : s);
  }
  function playSound() {
    const audio = new Audio("/assets/audio/notification.mp3");
    audio.play();
  }

  function toggle() {
    editMode = !editMode;
    minInput = null;
    secInput = null;
  }

  function setTimer() {
    let timer = 0;
    timer = secInput && parseInt(secInput);
    if (parseInt(minInput)) timer += minInput && parseInt(minInput) * 60;
    editMode = false;
    targetTime = +new Date() + timer * 1000;
    setDisplayTime();
    timerLogic(timer);
  }

  const onKeyup = (e) => e.key === "Enter" && setTimer();
</script>

{#if editMode}
  <h1 class="timerBlock">
    <input
      type="number"
      max="180"
      class="mf timerInput"
      bind:value={minInput}
      on:keyup={onKeyup}
    />:<input
      type="number"
      max="59"
      class="mf timerInput"
      bind:value={secInput}
      on:keyup={onKeyup}
    />
  </h1>
{:else}
  <h1 on:click={toggle} class="clock">
    {displayTime}
    <img
      on:click={toggle}
      class="delete timerIcons"
      src="/assets/svg/delete.svg"
      alt="Delete"
    />
  </h1>
{/if}
