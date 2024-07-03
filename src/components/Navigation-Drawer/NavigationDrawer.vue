<script setup lang="ts">
import { provide, ref } from 'vue'

const activeState = ref(false)
function setState() {
  activeState.value = !activeState.value
}

provide(/* key */ 'state', /* value */ { activeState, setState })
</script>
<template>
  <div id="hambergurIcon" @click="setState">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      x="0px"
      y="0px"
      width="40"
      height="40"
      viewBox="0 0 50 50"
    >
      <path
        d="M 0 7.5 L 0 12.5 L 50 12.5 L 50 7.5 Z M 0 22.5 L 0 27.5 L 50 27.5 L 50 22.5 Z M 0 37.5 L 0 42.5 L 50 42.5 L 50 37.5 Z"
      ></path>
    </svg>
  </div>

  <slot v-if="activeState"> active state</slot>
</template>

<style scoped>
#heading {
  display: flex;
  justify-content: center;
  height: 100vh;
}
#heading p {
  font-size: 32px;
}
</style>
