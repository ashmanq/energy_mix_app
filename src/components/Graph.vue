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
      const input = [["Fuel", "%"]];
      this.graphData.generationmix.forEach((item, i) => {
        input.push([item.fuel, item.perc]);
      });

      console.log(input);
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
