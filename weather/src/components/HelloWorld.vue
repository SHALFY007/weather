<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="input" placeholder="Input city...">
    <input type="submit" @click="search" value='Find Weather'/>
    <h1>In {{ city }} now {{ weather }} Celcianc</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      infoLocation: '',
      infoWeather: '',
      input: ''
    }
  },
  computed: {
    city() {
      return this.infoLocation.name
    },
    weather() {
      return this.infoWeather.temp_c
    }
  },
  props: {
    msg: String
  },
  methods: {
    search() {
      fetch(`http://api.weatherapi.com/v1/current.json?key=c2ecdba7a8a648009b4173326222812&q=${this.input}&aqi=no`)
    .then(a => a.json())
    .then(data =>  data.location)
    .then(res => this.infoLocation = res)

    fetch(`http://api.weatherapi.com/v1/current.json?key=c2ecdba7a8a648009b4173326222812&q=${this.input}&aqi=no`)
    .then(a => a.json())
    .then(data =>  data.current)
    .then(res => this.infoWeather = res)
    }
  },
  mounted() {
    fetch('http://api.weatherapi.com/v1/current.json?key=c2ecdba7a8a648009b4173326222812&q=London&aqi=no')
    .then(a => a.json())
    .then(data =>  data.location)
    .then(res => this.infoLocation = res)

    fetch('http://api.weatherapi.com/v1/current.json?key=c2ecdba7a8a648009b4173326222812&q=London&aqi=no')
    .then(a => a.json())
    .then(data =>  data.current)
    .then(res => this.infoWeather = res)
  }
}
</script>
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
