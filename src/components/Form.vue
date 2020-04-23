<template lang="html">
  <div class="">
    <label for="start-date">Start Date</label>
    <input v-model="startDate" type="date" name="start-date" value="">
    <label for="finish-date">Finish Date</label>
    <input v-model="endDate" type="date" name="finish-date" value="">
    <button v-on:click="sendDates" type="button" name="search">Search</button>
  </div>
</template>

<script>

import {eventBus} from '../main.js';

export default {
  name: 'form-view',
  data() {
    return {
      startDate:"",
      endDate:""
    }
  },
  methods: {
    sendDates: function() {
      if(this.startDate && this.endDate) {
        const start = new Date(this.startDate);
        const end = new Date(this.endDate);
        const dates = {
          startDate: start.toISOString(),
          endDate: end.toISOString()
        }
        eventBus.$emit('dates', dates);
      }

    },
  }

}
</script>

<style lang="css" scoped>
</style>
