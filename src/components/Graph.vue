<template lang="html">
  <GChart
    type="ColumnChart"
    :data="chartData"
    :options="chartOptions"

  />
</template>

<script>
import { GChart } from 'vue-google-charts';

export default {
  name:"graph-view",
  props:['graphData'],
  data() {
    return {
      inputData: this.graphData,
      chartData: this.populateChart(),
      chartOptions: {
        chart: {
          title: 'Energy Mix',
          subtitle: '%'
        }
      }
    };
  },
  methods: {
    populateChart: function(){
      const input = [];
      // if(Array.isArray(this.graphData)==false){
      input.push([["Fuel", "%"]]);
      this.graphData.generationmix.forEach((item, i) => {
        input.push([item.fuel, item.perc]);
      });
    // }
    // else {
    //   input.push([["Day", "Fuel", "%" ]]);
    //   this.graphData.forEach((item, i) => {
    //     item.forEach((item, i) => {
    //       input.push([item.from, item.fuel, item.perc])
    //     });
    //
    //   });
    //
    // }
    return input;
  }


  },

  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
