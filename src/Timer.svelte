<script>
    let timer = 0;
    let displayTime = ''; 
    let editMode = true;

    let minInput, secInput;

    function timerLogic(timer) {
        const timerInterval = setInterval(() => {
        if(timer)
            timer -= 1;
        let m = parseInt(timer / 60);
        let s =  timer % 60;
        displayTime = (m < 10 ? '0'+m : m) +':'+ (s < 10 ? '0'+s : s);
        timer === 0 && clearInterval(timerInterval)
        timer === 0 && !editMode && playSound();
    }, 1000);
    }
    
    timerLogic(timer);
    function playSound() {
        const audio = new Audio('/assets/audio/notification.mp3');
        audio.play();
    }

    function toggle() {
        editMode = !editMode;
    }

    function setTimer() {
        let timer = 0;
        timer = secInput && parseInt(secInput);
        if(parseInt(minInput))
            timer += minInput && (parseInt(minInput) * 60);
        editMode = false;
        timerLogic(timer);
    }
    function onKeyup(e) {
        if(e.key === 'Enter') {
            setTimer();
        }
    }

</script>
{#if editMode}
<h1 class="timerBlock">
    <!-- <div class="timerBlock"> -->
    <input type="number" max="180" class="mf timerInput" bind:value={minInput} on:keyup={onKeyup} />:<input type="number" max="59" class="mf timerInput" bind:value={secInput} on:keyup={onKeyup}/>
    <!-- <img class="delete timerIcons" src="/assets/svg/thumb-up.svg" alt="Save" on:click={setTimer}> -->
    <!-- <img on:click={toggle} class="delete timerIcons" src="/assets/svg/delete.svg" alt="Delte"> -->
<!-- </div> -->
</h1>
{:else}
<h1 on:click={toggle} class="clock">{displayTime}
    </h1>
{/if}