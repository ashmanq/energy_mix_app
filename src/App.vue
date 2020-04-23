<template>
  <div id="app">
    <p>{{ energymix }}</p>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      energymix: []
    }
  },
  mounted(){
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(response => response.json())
    .then(data => this.energymix = data)
  },
  components: {

  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
