<template lang="html">
  <GChart
    v-bind:type="chartType"
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
      chartType: "PieChart",
      // chartData: this.populateChart(),
      chartOptions: {
        chart: {
          title: 'Energy Mix',
          subtitle: '%'
        }
      }
    };
  },
  computed: {
    chartData: function(){
      if(Array.isArray(this.graphData)==false){
        const input = ([["Fuel", "%"]]);
        this.graphData.generationmix.forEach((item, i) => {
          input.push([item.fuel, item.perc]);
        });
      return input;
      }
      else {
        // a data table type variable is created (for Google charts object)
        const data = new google.visualization.DataTable();

        this.chartType = "LineChart";
        data.addColumn('date', 'Date');

        this.graphData[0].generationmix.forEach((item, i) => {
          data.addColumn('number', item.fuel);
        });


        this.graphData.forEach((item, i) => {
          const date = new Date(item.from);
          const row=[date];
          item.generationmix.forEach((daygen, i) => {
            row.push(daygen.perc);
          });
          data.addRow(row);

        });
        console.log(data);
        return data;

      }
    }
  },

  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
</style>
