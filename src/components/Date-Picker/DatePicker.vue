<script setup lang="ts">
import MonthPicker from './MonthPicker.vue'
import DateLabel from './DateLabel.vue'
import YearPicker from './YearPicker.vue'
import { computed, ref, watch, watchEffect } from 'vue'
import { eachDayOfInterval, endOfMonth, getDay, startOfMonth } from 'date-fns'

// let currentDate = ref(1)
let currentMonthModel = ref(1)
let currentYearModel = ref(2024)
let now = ref()
watchEffect(() => {
  now.value = new Date(currentYearModel.value, currentMonthModel.value - 1, 1).toLocaleDateString()
})

watch(currentMonthModel, () => changeDate(1))
watch(currentYearModel, () => changeDate(1))

function changeDate(date: number) {
  now.value = `${currentYearModel.value}/${currentMonthModel.value}/${date}`
}
const daysInMonth = computed(() => {
  const start = startOfMonth(now.value)
  const end = endOfMonth(now.value)
  return eachDayOfInterval({ start, end }).map((date) => date.getDate())
})

const emptyDays = computed(() => {
  const firstDayOfMonth = getDay(startOfMonth(now.value))
  const placeholderArray = []
  for (let i = 0; i < firstDayOfMonth; i++) {
    placeholderArray.push(i)
  }
  return placeholderArray
})
</script>

<template>
  <div id="main-main">
    <div id="datePickerContainer">
      <p>select date</p>
      <DateLabel id="selectedDate">{{ now }} </DateLabel>
      <div class="containerMonthAndYear">
        <div class="monthSelector">
          <MonthPicker v-model:currentMonthModel="currentMonthModel"> </MonthPicker>
        </div>
        <div class="yearSelector">
          <YearPicker v-model:currentYearModel="currentYearModel"></YearPicker>
        </div>
      </div>
      <div class="dayContainer">
        <span
          v-for="day in ['S', 'M', 'T', 'W', 'T', 'F', 'S']"
          v-bind:key="day"
          v-text="day"
        ></span>
      </div>
      <div class="dateContainer">
        <span v-for="date in emptyDays" v-bind:key="date"></span>
        <span
          v-for="date in daysInMonth"
          v-bind:key="date"
          v-text="date"
          @click="changeDate(date)"
        ></span>
      </div>
    </div>
  </div>
</template>

<style scooped>
html {
  margin: 0;
  padding: 0;
}

body {
  color: #080357;
}

#datePickerContainer > p {
  padding: 20px 0 0 20px;
}

#selectedDate {
  padding: 0 0 10px 20px;
}

#main-main {
  display: flex;
  /* justify-content: center; */
  padding-top: 10%;
  /* height: 100vh; */
}

#datePickerContainer {
  display: block;
  background-color: #ff9f1c;
  width: 500px;
  height: 550px;
  border-radius: 20px;
}

.dayContainer {
  display: grid;
  grid-template-columns: auto auto auto auto auto auto auto;
  background-color: #ffc15e;

  border: 1px solid black;
}

.dayContainer span,
.dateContainer span {
  padding: 25px;
  font-size: 20px;
}

.dateContainer {
  border: 1px solid black;
  display: grid;
  border-radius: 0 0 20px 20px;
  background-color: #ff9f1c;
  grid-template-columns: auto auto auto auto auto auto auto;
  grid-template-rows: auto auto auto auto auto;
}

.dateContainer span:hover {
  background-color: white;
  border-radius: 30% 0 30% 0;
}

.containerMonthAndYear {
  display: flex;
  justify-content: space-evenly;
}
</style>
