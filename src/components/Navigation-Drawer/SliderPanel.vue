<script setup lang="ts">
import { inject } from 'vue'

const { state, setState } = inject('state')
</script>
<template>
  <div id="slider">
    <ul>
      <li><a href="#">About</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Clients</a></li>
      <li><a href="#">Contact</a></li>
      <li>
        <span @click="setState">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            x="0px"
            y="0px"
            width="30"
            height="30"
            viewBox="0 0 30 30"
          >
            <path
              d="M 7 4 C 6.744125 4 6.4879687 4.0974687 6.2929688 4.2929688 L 4.2929688 6.2929688 C 3.9019687 6.6839688 3.9019687 7.3170313 4.2929688 7.7070312 L 11.585938 15 L 4.2929688 22.292969 C 3.9019687 22.683969 3.9019687 23.317031 4.2929688 23.707031 L 6.2929688 25.707031 C 6.6839688 26.098031 7.3170313 26.098031 7.7070312 25.707031 L 15 18.414062 L 22.292969 25.707031 C 22.682969 26.098031 23.317031 26.098031 23.707031 25.707031 L 25.707031 23.707031 C 26.098031 23.316031 26.098031 22.682969 25.707031 22.292969 L 18.414062 15 L 25.707031 7.7070312 C 26.098031 7.3170312 26.098031 6.6829688 25.707031 6.2929688 L 23.707031 4.2929688 C 23.316031 3.9019687 22.682969 3.9019687 22.292969 4.2929688 L 15 11.585938 L 7.7070312 4.2929688 C 7.5115312 4.0974687 7.255875 4 7 4 z"
            ></path>
          </svg>
        </span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
body {
}
#slider {
  background-color: #008f8c;
  width: 200px;
  height: 90vh;
  position: fixed;
  top: 10px;
  left: 0;
  z-index: 1000;
  transition: all 0.5s ease-in-out;
  border-radius: 0 2em 2em 0;
  padding: 30px;
  font-family: 'Jersey 25 Charted', sans-serif;
  font-weight: 400;
  font-style: normal;
  font-size: 1.75em;
  /*



  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  cursor: pointer;
  transition: all 0.5s ease-in-out; */
}
ul {
  list-style: none;
  text-decoration: none;
}
#slider li {
  padding-bottom: 2.5em;
}
#slider li a {
  color: white;
}
#slider li span {
  padding-left: 30px;
  font-weight: 900;
}
</style>
