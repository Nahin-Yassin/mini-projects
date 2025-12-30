<script setup>
import { ref } from 'vue'
let waiting = ref(0)

function waitingTime(delay = 5500) {
  waiting = Math.floor(Math.random() * delay) + 3000
  console.log(waiting)
  setTimeout(() => {
    console.log(`Delayed for ${waiting} ms`)
  }, delay)
}
waitingTime()
</script>
<template>
  <div class="container">
    <p>
      Reaction time test <br />
      click below to start
    </p>
    <div class="game_box" v-if="waitingTime" @click="waitingTime">
      <div class="for_green">
        <p>wait for green</p>
      </div>
    </div>
  </div>
</template>

<style>
.container {
  width: 500px;
  height: 500px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border: solid var(--clr-accent);
}
.game_box {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: red;
  width: 350px;
  height: 350px;
}

.for_green {
  background-color: green;
  width: 300px;
  height: 300px;
}
</style>
