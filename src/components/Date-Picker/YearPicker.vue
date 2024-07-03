<script setup lang="ts">
let start = 1900,
  end = 3000
const year: number[] = range(start, end)
function range(start: number, end: number) {
  var ans = []
  for (let i = start; i <= end; i++) {
    ans.push(i)
  }
  return ans
}
let yearModel = defineModel('currentYearModel')
</script>

<template>
  <select name="year" id="yearID" v-model="yearModel">
    <option
      v-for="tempCurrentYear in year"
      v-bind:key="tempCurrentYear"
      v-text="tempCurrentYear"
    ></option>
  </select>
</template>

<style scoped>
#yearID {
  padding: 8px;
  border-radius: 5px;
  font-size: 16px;
}
</style>
