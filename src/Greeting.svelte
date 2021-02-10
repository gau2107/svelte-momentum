<script>
    import * as mantras from "../public/mantras.json"
    let greeting = null;
    let mantra = mantras.default[~~(Math.random() * mantras.default.length)];
    let displayGreeting = true;

    setInterval(() => {
        displayGreeting = !displayGreeting;
    }, 15000);

    getGreetingText();


    function getGreetingText() {
        let hrs = new Date().getHours();
        if (hrs <= 11) {
            greeting = "Good Morning";
        } else if (hrs === 12) {
            greeting = "Good Noon";
        } else if (hrs >= 13 && hrs <= 16) {
            greeting = "Good Afternoon";
        } else {
            greeting = "Good Evening";
        }
    }
</script>
<h1 class="greeting">{displayGreeting ? greeting : mantra}</h1>
