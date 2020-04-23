<template lang="html">
  <div class="">
    <h2>Details</h2>
    <p>From: {{energymix.from}} </p>
    <p>To: {{ energymix.to  }}</p>
    <p v-for="energy in energymix.generationmix">{{ energy.fuel }} {{energy.perc}}%</p>
  </div>
</template>

<script>
export default {
  name:'details-view',
  props:['energymix'],
  data() {
    return {

    }
  }
}
</script>

<style lang="css" scoped>
</style>
