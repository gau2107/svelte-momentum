<script>
    let timer = 1500;
    let displayTime = ''; 
    
    const pomodoro = setInterval(() => {
        timer -= 1;
        let m = parseInt(timer / 60);
        let s =  timer % 60;
        displayTime = (m < 10 ? '0'+m : m) +':'+ (s < 10 ? '0'+s : s);
        timer === 0 && playSound();
        timer === 0 && clearInterval(pomodoro)
    }, 1000);

    function playSound() {
        const audio = new Audio('/assets/audio/notification.mp3');
        audio.play();
    }

</script>
{#if displayTime}
<h1 class="clock">{displayTime}</h1>
{/if}