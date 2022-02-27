<script>
    // FIXME always error
    //     function successCallback (position) {
    //         console.log(position.coords.latitude);
    //         console.log(position.coords.longitude);
    //     }
    //     function error() {
    //     console.log('Unable to retrieve your location');
    //   }

    //   navigator.geolocation.getCurrentPosition(successCallback, error);
    let weather = null;
    getLocation();

    function getLocation() {
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(getCurrentWeather);
        } else { 
            console.log("Geolocation is not supported by this browser.");
        }
    }

    async function getCurrentWeather(position) {
        const res = await fetch(
            `http://api.openweathermap.org/data/2.5/weather?lat=${position.coords.latitude}&lon=${position.coords.longitude}&appid=${process.env.WEATHER_API_KEY}`,
            {
                method: "GET",
                accept: "application/json",
            }
        );
        let resInJson = await res.json();
        weather = {...resInJson.main, ...resInJson.weather[0]};
        weather = {...weather, feels_like: convertFromKToC(weather.feels_like), metric: 'C'};
    }

    function toggle() {
        let t = weather.metric === 'C' ?
            (weather.feels_like * 9/5) + 32 :
            (weather.feels_like - 32) * 5/9;
        t= t.toFixed(0);
        weather = {...weather, feels_like: t,
            metric: weather.metric === 'C' ? 'F': 'C'};
    }

    function convertFromKToC(tempInKelvin) {
        return (tempInKelvin - 273.15).toFixed(0);
    }

</script>
{#if weather}
<div class="weather">
    <img src={`https://openweathermap.org/img/w/${weather.icon}.png`} alt={weather.main}/>
    <span on:click={toggle}>{weather.feels_like}°{weather.metric}</span>
    </div>
{/if}
