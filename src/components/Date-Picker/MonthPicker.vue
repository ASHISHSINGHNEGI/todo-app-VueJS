<script setup lang="ts">
// let months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
let monthModel = defineModel('currentMonthModel')
</script>

<template>
  <select name="" id="monthID" v-model="monthModel">
    <option
      v-for="tempCurrentMonth in 12"
      v-bind:key="tempCurrentMonth"
      v-text="tempCurrentMonth"
    ></option>
  </select>
</template>

<style scoped>
#monthID {
  padding: 8px;
  border-radius: 5px;
  font-size: 16px;
}
</style>
