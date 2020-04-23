<template>
  <div id="app">
    <h1>Energy Mix App</h1>
    <!-- <p>{{ energymix }}</p> -->
    <detail-view v-if="energymix" :energymix="energymix"></detail-view>
  </div>
</template>

<script>

import Details from './components/Details.vue';

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
    .then(result => this.energymix = result.data)
  },
  components: {
    "detail-view": Details
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
