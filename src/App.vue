<template>
  <div class="" id="app">
    <h1>Energy Mix App</h1>
    <div class="container">


    <section class="detail">
      <detail-view v-if="energymix" :energymix="energymix"></detail-view>

    </section>
    <section class="graph">
      <graph-view v-if="energymix" :graphData="energymix"></graph-view>
    </section>
      </div>
  </div>
</template>

<script>

import Details from './components/Details.vue';
import Graph from './components/Graph.vue';

export default {
  name: 'App',
  data(){
    return{
      energymix: null,
    }
  },
  mounted(){
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(response => response.json())
    .then(result => this.energymix = result.data)
  },
  components: {
    "detail-view": Details,
    "graph-view": Graph
  }
}
</script>

<style>
h1 {
  text-align: center;
}
.container {
  display:flex;

  justify-content: space-around;
  /* flex-direction: column; */
}
 .detail{
   /* width:50%; */
 }
 .graph{
   display: flex;
   /* width:100%; */
 }
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
