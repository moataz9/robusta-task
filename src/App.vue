<template>
  <div id="app">
    <AppHeader app-name="instaweather"></AppHeader>
    <AppInfo
      v-if="data"
      :appTown="data.name"
      :iconSource="`http://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`"
      :weatherDescription="data.weather[0].description"
      :degree="data.main.temp"
      :dayDegree="data.main.temp_max"
      :nightDegree="data.main.temp_min"
      :dayStatus="data.weather[0].main"
    ></AppInfo>
  </div>
</template>

<script>
import AppInfo from './components/AppInfo.vue'
import AppHeader from './components/AppHeader.vue'

// App.vue
export default {
  name: 'App',
  components: { AppInfo, AppHeader },
  data() {
    return {
      lat: null,
      lon: null,
      open_weather_url: 'https://api.openweathermap.org/data/2.5/weather',
      open_weather_api_key: '41c096cea92a482759e884f2e05ae7e5',
      data: null,
    }
  },
  methods: {
    async getData() {
      try {
        this.data = await (
          await fetch(
            `${this.open_weather_url}?lat=${this.lat}&lon=${this.lon}&appid=${this.open_weather_api_key}`
          )
        ).json()
      } catch (err) {
        console.log(err)
      }
    },
  },
  created() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(position => {
        this.lat = position.coords.latitude
        this.lon = position.coords.longitude
        this.getData()
      })
    }
  },
}
</script>

<style lang="scss">
body {
  background-image: url('./assets/images/Background.png');
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  font-family: 'Work Sans';
  min-height: 100vh;
}

#app {
  @media (min-width: 787px) {
    max-width: 90%;
    margin: 0 auto;
  }
}
</style>
