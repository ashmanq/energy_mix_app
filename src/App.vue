<template>
  <div id="app">

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
    .then(data => console.log(data))
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
