<template>
  <div id="app">
    <AppHeader app-name="instaweather"></AppHeader>
    <AppInfo
      appTown="new Cairo"
      iconSource="@/assets/images/test-icon.png"
      weatherDescription="this weather desc"
      degree="30"
      dayDegree="30"
      nightDegree="20"
      dayStatus="the weather is coludy"
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
      long: null,
      api_key: 'a177f8481c31fa96c3f95ad4f4f84610',
    }
  },
  methods: {
    getList() {
      this.axios
        .get(`https://api.darksky.net/forecast/${this.api_key}/${lat}, ${long}`)
        .then(response => {
          console.log(response.data)
        })
      // or
      this.$http
        .get(`https://api.darksky.net/forecast/${this.api_key}/${lat}, ${long}`)
        .then(response => {
          console.log(response.data)
        })
    },
  },
  created() {
    if (navigator.geolocation) {
      let data =  navigator.geolocation.getCurrentPosition()
      this.lat = data.coords.latitude
      this.long = data.coords.longitude
    }
    console.log(lat, long);
  },
}
</script>

<style lang="scss">
body {
  background-image: url('./assets/images/Background.png');
  font-family: 'Work Sans';
}

#app {
  @media (min-width: 787px) {
    max-width: 90%;
    margin: 0 auto;
  }
}
</style>
