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
    getCurrentWeather();

    async function getCurrentWeather() {
        const res = await fetch(
            "http://api.openweathermap.org/data/2.5/weather?q=valsad&appid=831e6fa7b7ec4425ad07dc642847be20",
            {
                method: "GET",
                accept: "application/json",
            }
        );
        let resInJson = await res.json();
        console.log(resInJson);
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
<div>
    <h1 on:click={toggle}>{weather.feels_like}°{weather.metric}</h1>
    <!-- <h1>{weather.main}</h1> -->
    <img src={`http://openweathermap.org/img/w/${weather.icon}.png`} alt={weather.main}/>
    </div>
{/if}
